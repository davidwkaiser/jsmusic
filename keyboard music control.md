keyboard music control

<body>
    <div
        style="background:black; height:500px;"
        tabindex="1"
        onkeydown="setNote(event.key)"
        >

    </div>

</body>

<script>

    var audio_context = window.AudioContext || window.webkitAudioContext;

   var con = new audio_context();
   var osc = con.createOscillator();

   osc.connect(con.destination);
   osc.frequency.value = 600;

   osc.start();

   function setNote(key){
       if (key == "z")
       osc.frequency.value=261.63;
       if (key == "x")
       osc.frequency.value=293.66;
       if (key == "c")
       osc.frequency.value=329.63;
       if (key == "v")
       osc.frequency.value=349.23;
          }
</script>