

<body>


    <canvas id="position1" nx="position"></canvas>
    <canvas id="dial1" nx="dial"></canvas>

</body>

<script>

var audio_context = window.AudioContext || window.webkitAudioContext;
var con = new audio_context();

var osc = con.createOscillator();
var lfo = con.createOscillator();

var lfo_amp = con.createGain();
lfo_amp.gain.value = 200;

osc.frequency.value = 300;
lfo.frequency.value = 15;

lfo.connect(lfo_amp);
lfo_amp.connect(osc.frequency);
osc.connect(con.destination);

// osc.start();
// lfo.start();

var position1, dial1;

nx.onload = function(){
    position1.on('*', pos1Changed);
    dial1.on('*', dial1Changed);
};


function pos1Changed(data){
    osc.frequency.value = 1000 * data.x;
    lfo.frequency.value = 20* data.y;
}

function dial1Changed(data){
    lfo_amp.gain.value = data.value*400;
}





</script>