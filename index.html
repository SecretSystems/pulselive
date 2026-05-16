<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>PulseLive</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    background:black;
    overflow:hidden;
    font-family:Arial, sans-serif;
}

#app{
    width:100vw;
    height:100vh;
    position:relative;
    overflow:hidden;
}

video{
    position:absolute;
    width:100%;
    height:100%;
    object-fit:cover;
    top:0;
    left:0;
}

.overlay{
    position:absolute;
    top:30px;
    left:30px;
    color:white;
    z-index:10;
    text-shadow:0 0 20px rgba(0,0,0,0.7);
}

.bpm{
    font-size:90px;
    font-weight:bold;
    line-height:1;
}

.label{
    font-size:28px;
    margin-top:5px;
}

.zone{
    margin-top:10px;
    font-size:24px;
}

.zone-bar{
    display:flex;
    gap:8px;
    margin-top:20px;
}

.zone-segment{
    width:55px;
    height:16px;
    border-radius:999px;
    background:rgba(255,255,255,0.2);
}

.active{
    background:#ff0033;
}

.controls{
    position:absolute;
    bottom:40px;
    left:50%;
    transform:translateX(-50%);
    z-index:20;
    display:flex;
    gap:15px;
}

button{
    border:none;
    border-radius:16px;
    padding:16px 26px;
    background:#ff0033;
    color:white;
    font-size:18px;
    cursor:pointer;
    font-weight:bold;
}

button:hover{
    opacity:0.9;
}

.status{
    position:absolute;
    top:30px;
    right:30px;
    color:white;
    z-index:20;
    font-size:18px;
    background:rgba(0,0,0,0.4);
    padding:10px 14px;
    border-radius:12px;
    backdrop-filter:blur(10px);
}
</style>
</head>

<body>

<div id="app">

    <video id="camera" autoplay muted playsinline></video>

    <div class="overlay">
        <div class="bpm" id="bpm">92</div>
        <div class="label">BPM</div>
        <div class="zone" id="zoneText">Zone 2 - Fat Burn</div>

        <div class="zone-bar">
            <div class="zone-segment" id="z1"></div>
            <div class="zone-segment" id="z2"></div>
            <div class="zone-segment" id="z3"></div>
            <div class="zone-segment" id="z4"></div>
            <div class="zone-segment" id="z5"></div>
        </div>
    </div>

    <div class="status" id="status">
        Waiting for heart rate monitor
    </div>

    <div class="controls">
        <button id="cameraBtn">
            Start Camera
        </button>

        <button id="connectBtn">
            Connect Heart Rate Monitor
        </button>
    </div>

</div>

<script>

const video = document.getElementById('camera')
const bpmText = document.getElementById('bpm')
const zoneText = document.getElementById('zoneText')
const statusText = document.getElementById('status')

const zones = [
    document.getElementById('z1'),
    document.getElementById('z2'),
    document.getElementById('z3'),
    document.getElementById('z4'),
    document.getElementById('z5'),
]

async function startCamera(){

    try{

        const stream = await navigator.mediaDevices.getUserMedia({
            video:true,
            audio:true
        })

        video.srcObject = stream

    }catch(error){

        alert('Camera permission denied.')

        console.error(error)
    }
}

document.getElementById('cameraBtn')
.addEventListener('click', startCamera)

function updateHeartRate(hr){

    bpmText.innerText = hr

    let zone = 1
    let zoneName = 'Recovery'

    if(hr < 100){
        zone = 1
        zoneName = 'Recovery'
    }
    else if(hr < 120){
        zone = 2
        zoneName = 'Fat Burn'
    }
    else if(hr < 140){
        zone = 3
        zoneName = 'Cardio'
    }
    else if(hr < 160){
        zone = 4
        zoneName = 'Peak'
    }
    else{
        zone = 5
        zoneName = 'Maximum'
    }

    zoneText.innerText = `Zone ${zone} - ${zoneName}`

    zones.forEach((z, index)=>{

        z.classList.remove('active')

        if(index < zone){
            z.classList.add('active')
        }
    })
}

async function connectHeartRate(){

    try{

        statusText.innerText = 'Searching for monitor...'

        const device = await navigator.bluetooth.requestDevice({
            filters:[
                {
                    services:['heart_rate']
                }
            ]
        })

        statusText.innerText = `Connected: ${device.name}`

        const server = await device.gatt.connect()

        const service = await server.getPrimaryService('heart_rate')

        const characteristic = await service.getCharacteristic(
            'heart_rate_measurement'
        )

        await characteristic.startNotifications()

        characteristic.addEventListener(
            'characteristicvaluechanged',
            handleHeartRateChanged
        )

        function handleHeartRateChanged(event){

            const value = event.target.value

            const hr = value.getUint8(1)

            updateHeartRate(hr)
        }

    }catch(error){

        console.error(error)

        statusText.innerText = 'Connection failed'
    }
}

document.getElementById('connectBtn')
.addEventListener('click', connectHeartRate)

setInterval(()=>{

    const current = parseInt(bpmText.innerText)

    const fake = current + Math.floor(Math.random()*6-3)

    updateHeartRate(fake)

},2000)

</script>

</body>
</html>
