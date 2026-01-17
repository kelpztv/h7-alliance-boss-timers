export default function BossTimerApp(){
  const defaultBosses=[
    {name:'Dark Reaper',respawn:1800,icon:'https://i.imgur.com/1Xq9BiD.png'},
    {name:'Night Stalker',respawn:2700,icon:'https://i.imgur.com/6o5V7G6.png'},
    {name:'Hell Beast',respawn:3600,icon:'https://i.imgur.com/tV8Z8bC.png'}
  ];

  const channel = React.useMemo(()=>new BroadcastChannel('h7-boss-sync'),[]);

  const [bosses,setBosses]=React.useState(()=>JSON.parse(localStorage.getItem('bosses')||JSON.stringify(defaultBosses)));
  const [kills,setKills]=React.useState(()=>{
    const fromUrl=window.location.hash.startsWith('#share=')?JSON.parse(atob(window.location.hash.replace('#share=',''))):null;
    return fromUrl||JSON.parse(localStorage.getItem('kills')||'{}');
  });

  React.useEffect(()=>localStorage.setItem('bosses',JSON.stringify(bosses)),[bosses]);
  React.useEffect(()=>{
    localStorage.setItem('kills',JSON.stringify(kills));
    channel.postMessage({kills});
  },[kills]);

  React.useEffect(()=>{
    channel.onmessage=e=>{if(e.data.kills) setKills(e.data.kills)};
  },[]);

  function start(name){setKills({...kills,[name]:Date.now()});}
  function share(){window.location.hash='share='+btoa(JSON.stringify(kills));navigator.clipboard.writeText(window.location.href);} 

  function addBoss(){
    const name=prompt('Boss name');
    const min=parseInt(prompt('Respawn minutes'))||30;
    const icon=prompt('Icon image URL');
    if(name) setBosses([...bosses,{name,respawn:min*60,icon}]);
  }

  function fmt(sec){const m=Math.floor(sec/60),s=sec%60;return `${m}m ${s}s`;}

  return (
    <div className="min-h-screen bg-black text-white p-6">
      <h1 className="text-3xl mb-4">H7 Alliance Boss Timer</h1>
      <div className="flex gap-2 mb-4">
        <button onClick={share} className="bg-gray-700 px-3 py-1 rounded">Share Timers</button>
        <button onClick={addBoss} className="bg-gray-700 px-3 py-1 rounded">Add Boss</button>
      </div>
      {bosses.map(b=>{
        const last=kills[b.name];
        const remain=last?Math.max(0,Math.floor((last+b.respawn*1000-Date.now())/1000)):0;
        if(remain===0&&last){
          try{new Audio('https://actions.google.com/sounds/v1/alarms/alarm_clock.ogg').play()}catch{}
        }
        return (
          <div key={b.name} className="bg-gray-900 border border-gray-700 rounded p-3 mb-2 flex justify-between items-center">
            <div className="flex items-center gap-3">
              {b.icon && <img src={b.icon} className="w-10 h-10 rounded"/>}
              <div>
                <div className="font-bold">{b.name}</div>
                {last? <div>Next in {fmt(remain)}</div>:<div>No timer running</div>}
              </div>
            </div>
            <button onClick={()=>start(b.name)} className="bg-gray-700 px-2 py-1 rounded">{remain===0&&last?'Ready':'Start'}</button>
          </div>
        )})}
      <p className="text-sm text-gray-400 mt-4">Realtime sync works between open browsers via BroadcastChannel + shared links.</p>
    </div>
  )
}
