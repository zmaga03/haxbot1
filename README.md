// Stats: "Auth" : '["0-Games", "1-Wins", "2-Draws", "3-Losses", "4-Winrate", "5-Goals", "6-Assists", "7-GK", "8-CS", "9-CS%", "10-Role", "11-Nick"]'

/* VARIABLES */

/* ROOM */

const roomName = "Futsal 3v3";
const botName = "HaxBot";
const maxPlayers = 12;
const roomPublic = false;
const geo = [{"code": "DE", "lat": 51.1, "lon": 10.4}, {"code": "FR", "lat": 46.2, "lon": 2.2}, {"code": "PL", "lat": 51.9, "lon": 19.1}, {"code": "GB", "lat": 55.3, "lon": -3.4}, {"code": "PT", "lat": 39.3, "lon": -8.2}];

const room = HBInit({ roomName: roomName, maxPlayers: maxPlayers, public: roomPublic, playerName: botName, geo: geo[0] });

const scoreLimitClassic = 3;
const scoreLimitBig = 3;
const timeLimitClassic = 3;
const timeLimitBig = 3;

room.setTeamsLock(true);

var adminPassword = 1000 + getRandomInt(9000);
console.log("adminPassword : " + adminPassword);

/* STADIUM */

const playerRadius = 15;
var ballRadius = 10;
const triggerDistance = playerRadius + ballRadius + 0.01;
var aloneMap = '{"name":"Futsal No Goals","width":420,"height":200,"bg":{"type":"hockey","width":368,"height":171,"kickOffRadius":65},"vertexes":[{"x":-368,"y":171,"cMask":["ball"]},{"x":-368,"y":65,"cMask":["ball"]},{"x":-368,"y":-65,"cMask":["ball"]},{"x":-368,"y":-171,"cMask":["ball"]},{"x":368,"y":171,"cMask":["ball"]},{"x":368,"y":65,"cMask":["ball"]},{"x":368,"y":-65,"cMask":["ball"]},{"x":368,"y":-171,"cMask":["ball"]},{"x":0,"y":65,"bCoef":0,"cMask":[]},{"x":0,"y":-65,"bCoef":0,"cMask":[]},{"x":368,"y":171,"cMask":["ball"]},{"x":368,"y":-171,"cMask":["ball"]},{"x":0,"y":171,"bCoef":0,"cMask":[]},{"x":0,"y":-171,"bCoef":0,"cMask":[]},{"x":0,"y":65,"bCoef":0,"cMask":[]},{"x":0,"y":-65,"bCoef":0,"cMask":[]},{"x":377,"y":-65,"cMask":["ball"]},{"x":377,"y":-171,"cMask":["ball"]},{"x":-377,"y":-65,"cMask":["ball"]},{"x":-377,"y":-171,"cMask":["ball"]},{"x":-377,"y":65,"cMask":["ball"]},{"x":-377,"y":171,"cMask":["ball"]},{"x":377,"y":65,"cMask":["ball"]},{"x":377,"y":171,"cMask":["ball"]},{"x":0,"y":65,"bCoef":0,"cMask":[]},{"x":0,"y":-65,"bCoef":0,"cMask":[]},{"x":-368.53340356886,"y":-62.053454903872,"bCoef":0.1,"cMask":["red","blue","ball"]},{"x":-400.05760771891,"y":-62.053454903872,"bCoef":0.1,"cMask":["red","blue","ball"]},{"x":-400.05760771891,"y":64.043361696331,"bCoef":0.1,"cMask":["red","blue","ball"]},{"x":-368.53340356886,"y":64.043361696331,"bCoef":0.1,"cMask":["red","blue","ball"]},{"x":368.09926357786,"y":63.94882446641,"bCoef":0.1,"cMask":["red","blue","ball"]},{"x":400,"y":64,"bCoef":0.1,"cMask":["red","blue","ball"]},{"x":400,"y":-61.927767991658,"bCoef":0.1,"cMask":["red","blue","ball"]},{"x":368.9681846993,"y":-62.144998272018,"bCoef":0.1,"cMask":["red","blue","ball"]},{"x":-368,"y":-142.37229643041,"bCoef":0.1,"cMask":[]},{"x":-260.90035258157,"y":-50.168480548544,"bCoef":0.1,"cMask":[]},{"x":-368,"y":-160.81305960678,"bCoef":0.1,"cMask":[]},{"x":-358.5379338963,"y":-171,"bCoef":0.1,"cMask":[]},{"x":-368,"y":141.33175243687,"bCoef":0.1,"cMask":[]},{"x":-260.90035258157,"y":49.127936555002,"bCoef":0.1,"cMask":[]},{"x":-368,"y":159.77251561324,"bCoef":0.1,"cMask":[]},{"x":-358.5379338963,"y":171,"bCoef":0.1,"cMask":[]},{"x":368,"y":159.77251561324,"bCoef":0.1,"cMask":[]},{"x":358.36266315432,"y":171,"bCoef":0.1,"cMask":[]},{"x":368,"y":-160.81305960678,"bCoef":0.1,"cMask":[]},{"x":358.36266315432,"y":-171,"bCoef":0.1,"cMask":[]},{"x":368,"y":-142.37229643041,"bCoef":0.1,"cMask":[]},{"x":260.72508183959,"y":-50.168480548544,"bCoef":0.1,"cMask":[]},{"x":368,"y":141.33175243687,"bCoef":0.1,"cMask":[]},{"x":260.72508183959,"y":49.127936555002,"bCoef":0.1,"cMask":[]},{"x":260.72508183959,"y":-50.168480548544,"bCoef":0.1,"cMask":[]},{"x":260.72508183959,"y":49.127936555002,"bCoef":0.1,"cMask":[]},{"x":-250.86909422732,"y":-1.2295321189394,"bCoef":0.1,"cMask":[]},{"x":-250.86909422732,"y":0.18898812539692,"bCoef":0.1,"cMask":[]},{"x":-250.86909422732,"y":-2.6480523632758,"bCoef":0.1,"cMask":[]},{"x":-250.86909422732,"y":1.6075083697333,"bCoef":0.1,"cMask":[]},{"x":-250.86909422732,"y":0.89824824756514,"bCoef":0.1,"cMask":[]},{"x":-250.86909422732,"y":-1.9387922411076,"bCoef":0.1,"cMask":[]},{"x":-250.86909422732,"y":1.9621384308174,"bCoef":0.1,"cMask":[]},{"x":-250.86909422732,"y":-3.0026824243599,"bCoef":0.1,"cMask":[]},{"x":250.69382348534,"y":-1.2295321189394,"bCoef":0.1,"cMask":[]},{"x":250.69382348534,"y":0.18898812539692,"bCoef":0.1,"cMask":[]},{"x":250.69382348534,"y":-2.6480523632758,"bCoef":0.1,"cMask":[]},{"x":250.69382348534,"y":1.6075083697333,"bCoef":0.1,"cMask":[]},{"x":250.69382348534,"y":0.89824824756514,"bCoef":0.1,"cMask":[]},{"x":250.69382348534,"y":-1.9387922411076,"bCoef":0.1,"cMask":[]},{"x":250.69382348534,"y":1.9621384308174,"bCoef":0.1,"cMask":[]},{"x":250.69382348534,"y":-3.0026824243599,"bCoef":0.1,"cMask":[]},{"x":-185.66591492467,"y":-1.2295321189394,"bCoef":0.1,"cMask":[]},{"x":-185.66591492467,"y":0.18898812539692,"bCoef":0.1,"cMask":[]},{"x":-185.66591492467,"y":-2.6480523632758,"bCoef":0.1,"cMask":[]},{"x":-185.66591492467,"y":1.6075083697333,"bCoef":0.1,"cMask":[]},{"x":-185.66591492467,"y":0.89824824756514,"bCoef":0.1,"cMask":[]},{"x":-185.66591492467,"y":-1.9387922411076,"bCoef":0.1,"cMask":[]},{"x":-185.66591492467,"y":1.9621384308174,"bCoef":0.1,"cMask":[]},{"x":-185.66591492467,"y":-3.0026824243599,"bCoef":0.1,"cMask":[]},{"x":185.49064418269,"y":-1.2295321189394,"bCoef":0.1,"cMask":[]},{"x":185.49064418269,"y":0.18898812539692,"bCoef":0.1,"cMask":[]},{"x":185.49064418269,"y":-2.6480523632758,"bCoef":0.1,"cMask":[]},{"x":185.49064418269,"y":1.6075083697333,"bCoef":0.1,"cMask":[]},{"x":185.49064418269,"y":0.89824824756514,"bCoef":0.1,"cMask":[]},{"x":185.49064418269,"y":-1.9387922411076,"bCoef":0.1,"cMask":[]},{"x":185.49064418269,"y":1.9621384308174,"bCoef":0.1,"cMask":[]},{"x":185.49064418269,"y":-3.0026824243599,"bCoef":0.1,"cMask":[]},{"x":-160.58776903904,"y":-159.39453936245,"bCoef":0.1,"cMask":[]},{"x":-160.58776903904,"y":-182.09086327183,"bCoef":0.1,"cMask":[]},{"x":-80.337702205015,"y":-159.39453936245,"bCoef":0.1,"cMask":[]},{"x":-80.337702205015,"y":-182.09086327183,"bCoef":0.1,"cMask":[]},{"x":160.41249829706,"y":-159.39453936245,"bCoef":0.1,"cMask":[]},{"x":160.41249829706,"y":-182.09086327183,"bCoef":0.1,"cMask":[]},{"x":80.162431463036,"y":-159.39453936245,"bCoef":0.1,"cMask":[]},{"x":80.162431463036,"y":-182.09086327183,"bCoef":0.1,"cMask":[]},{"x":-254.88159756902,"y":-171,"bCoef":0.1,"cMask":[]},{"x":-254.88159756902,"y":-182.09086327183,"bCoef":0.1,"cMask":[]},{"x":-371.91294503531,"y":-87.759267023458,"bCoef":0.1,"cMask":[]},{"x":-384.61920561736,"y":-87.759267023458,"bCoef":0.1,"cMask":[]},{"x":371.73767429333,"y":-87.759267023458,"bCoef":0.1,"cMask":[]},{"x":384.44393487538,"y":-87.759267023458,"bCoef":0.1,"cMask":[]},{"x":-371.91294503531,"y":86.718723029916,"bCoef":0.1,"cMask":[]},{"x":-384.61920561736,"y":86.718723029916,"bCoef":0.1,"cMask":[]},{"x":371.73767429333,"y":86.718723029916,"bCoef":0.1,"cMask":[]},{"x":384.44393487538,"y":86.718723029916,"bCoef":0.1,"cMask":[]},{"x":-254.88159756902,"y":171,"bCoef":0.1,"cMask":[]},{"x":-254.88159756902,"y":181.05031927829,"bCoef":0.1,"cMask":[]},{"x":254.70632682704,"y":-171,"bCoef":0.1,"cMask":[]},{"x":254.70632682704,"y":-182.09086327183,"bCoef":0.1,"cMask":[]},{"x":254.70632682704,"y":171,"bCoef":0.1,"cMask":[]},{"x":254.70632682704,"y":181.05031927829,"bCoef":0.1,"cMask":[]},{"x":369,"y":65,"cMask":["ball"]},{"x":369,"y":-65,"cMask":["ball"]},{"x":-370,"y":65,"cMask":["ball"]},{"x":-370,"y":-65,"cMask":["ball"]},{"x":371,"y":-65,"bCoef":0,"cMask":["ball"]},{"x":371,"y":-171,"bCoef":0,"cMask":["ball"]},{"x":371,"y":65,"bCoef":0,"cMask":["ball"]},{"x":371,"y":171,"bCoef":0,"cMask":["ball"]},{"x":-371,"y":65,"bCoef":0,"cMask":["ball"]},{"x":-371,"y":171,"bCoef":0,"cMask":["ball"]},{"x":-371,"y":-65,"bCoef":0,"cMask":["ball"]},{"x":-371,"y":-171,"bCoef":0,"cMask":["ball"]}],"segments":[{"v0":0,"v1":1,"vis":false,"cMask":["ball"]},{"v0":2,"v1":3,"vis":false,"cMask":["ball"]},{"v0":4,"v1":5,"vis":false,"cMask":["ball"]},{"v0":6,"v1":7,"vis":false,"cMask":["ball"]},{"v0":8,"v1":9,"bCoef":0,"curve":180,"curveF":6.123233995736766e-17,"cMask":[],"cGroup":["blueKO"]},{"v0":9,"v1":8,"bCoef":0,"curve":180,"curveF":6.123233995736766e-17,"cMask":[],"cGroup":["redKO"]},{"v0":1,"v1":0,"cMask":["ball"],"color":"FFFFFF"},{"v0":5,"v1":4,"cMask":["ball"],"color":"FFFFFF"},{"v0":2,"v1":3,"cMask":["ball"],"color":"FFFFFF"},{"v0":6,"v1":7,"cMask":["ball"],"color":"FFFFFF"},{"v0":0,"v1":10,"cMask":["ball"],"color":"FFFFFF"},{"v0":3,"v1":11,"cMask":["ball"],"color":"FFFFFF"},{"v0":12,"v1":13,"bCoef":0,"cMask":[],"color":"FFFFFF"},{"v0":8,"v1":9,"bCoef":0,"curve":180,"curveF":6.123233995736766e-17,"cMask":[],"color":"FFFFFF"},{"v0":15,"v1":14,"bCoef":0,"curve":180,"curveF":6.123233995736766e-17,"cMask":[],"color":"FFFFFF"},{"v0":2,"v1":1,"cMask":["ball"],"color":"FFFFFF"},{"v0":6,"v1":5,"cMask":["ball"],"color":"FFFFFF"},{"v0":16,"v1":17,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":18,"v1":19,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":20,"v1":21,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":22,"v1":23,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":26,"v1":27,"bCoef":0.1,"cMask":["red","blue","ball"],"color":"F8F8F8"},{"v0":27,"v1":28,"bCoef":0.1,"cMask":["red","blue","ball"],"color":"F8F8F8"},{"v0":28,"v1":29,"bCoef":0.1,"cMask":["red","blue","ball"],"color":"F8F8F8"},{"v0":30,"v1":31,"bCoef":0.1,"cMask":["red","blue","ball"],"color":"F8F8F8"},{"v0":31,"v1":32,"bCoef":0.1,"cMask":["red","blue","ball"],"color":"F8F8F8"},{"v0":32,"v1":33,"bCoef":0.1,"cMask":["red","blue","ball"],"color":"F8F8F8"},{"v0":34,"v1":35,"bCoef":0.1,"curve":94.0263701017,"curveF":0.9320849449101076,"cMask":[],"color":"F8F8F8"},{"v0":37,"v1":36,"bCoef":0.1,"curve":86.632306418889,"curveF":1.060575000344919,"cMask":[],"color":"F8F8F8"},{"v0":39,"v1":38,"bCoef":0.1,"curve":94.026370101699,"curveF":0.9320849449101238,"cMask":[],"color":"F8F8F8"},{"v0":35,"v1":39,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":40,"v1":41,"bCoef":0.1,"curve":86.632306418888,"curveF":1.0605750003449375,"cMask":[],"color":"F8F8F8"},{"v0":43,"v1":42,"bCoef":0.1,"curve":86.632306418884,"curveF":1.0605750003450118,"cMask":[],"color":"F8F8F8"},{"v0":44,"v1":45,"bCoef":0.1,"curve":86.632306418899,"curveF":1.0605750003447336,"cMask":[],"color":"F8F8F8"},{"v0":47,"v1":46,"bCoef":0.1,"curve":94.026370101699,"curveF":0.9320849449101238,"cMask":[],"color":"F8F8F8"},{"v0":48,"v1":49,"bCoef":0.1,"curve":94.026370101699,"curveF":0.9320849449101238,"cMask":[],"color":"F8F8F8"},{"v0":50,"v1":51,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":52,"v1":53,"bCoef":0.1,"curve":-179.99307079708004,"curveF":-0.000060468702819980624,"cMask":[],"color":"F8F8F8"},{"v0":53,"v1":52,"bCoef":0.1,"curve":-179.99781759386002,"curveF":-0.000019045086381751383,"cMask":[],"color":"F8F8F8"},{"v0":54,"v1":55,"bCoef":0.1,"curve":179.64823645332,"curveF":0.0030697256812038513,"cMask":[],"color":"F8F8F8"},{"v0":55,"v1":54,"bCoef":0.1,"curve":-179.64241331853003,"curveF":-0.003120542605465436,"cMask":[],"color":"F8F8F8"},{"v0":56,"v1":57,"bCoef":0.1,"curve":-179.97642676038004,"curveF":-0.00020571532626703233,"cMask":[],"color":"F8F8F8"},{"v0":57,"v1":56,"bCoef":0.1,"curve":-179.99075897601003,"curveF":-0.00008064314761547242,"cMask":[],"color":"F8F8F8"},{"v0":58,"v1":59,"bCoef":0.1,"curve":-179.93114244115003,"curveF":-0.0006008956307319741,"cMask":[],"color":"F8F8F8"},{"v0":59,"v1":58,"bCoef":0.1,"curve":-179.97051646743003,"curveF":-0.0002572923649102433,"cMask":[],"color":"F8F8F8"},{"v0":60,"v1":61,"bCoef":0.1,"curve":179.99869069543,"curveF":0.000011425837829318613,"cMask":[],"color":"F8F8F8"},{"v0":61,"v1":60,"bCoef":0.1,"curve":179.99939258776004,"curveF":0.000005300671752306162,"cMask":[],"color":"F8F8F8"},{"v0":62,"v1":63,"bCoef":0.1,"curve":-179.91173952837002,"curveF":-0.0007702180669602502,"cMask":[],"color":"F8F8F8"},{"v0":63,"v1":62,"bCoef":0.1,"curve":179.91186753664,"curveF":0.0007691009834080061,"cMask":[],"color":"F8F8F8"},{"v0":64,"v1":65,"bCoef":0.1,"curve":179.99528711105,"curveF":0.000041127714752444664,"cMask":[],"color":"F8F8F8"},{"v0":65,"v1":64,"bCoef":0.1,"curve":179.99743836358,"curveF":0.000022354494887865286,"cMask":[],"color":"F8F8F8"},{"v0":66,"v1":67,"bCoef":0.1,"curve":179.98626041101,"curveF":0.00011990053344777071,"cMask":[],"color":"F8F8F8"},{"v0":67,"v1":66,"bCoef":0.1,"curve":179.99175181595,"curveF":0.0000719789846157737,"cMask":[],"color":"F8F8F8"},{"v0":68,"v1":69,"bCoef":0.1,"curve":-179.95284437602004,"curveF":-0.0004115104728700557,"cMask":[],"color":"F8F8F8"},{"v0":69,"v1":68,"bCoef":0.1,"curve":179.95294709391,"curveF":0.0004106140900279739,"cMask":[],"color":"F8F8F8"},{"v0":70,"v1":71,"bCoef":0.1,"curve":179.95715750564,"curveF":0.0003738713105943949,"cMask":[],"color":"F8F8F8"},{"v0":71,"v1":70,"bCoef":0.1,"curve":179.89943871875,"curveF":0.0008775629541936324,"cMask":[],"color":"F8F8F8"},{"v0":72,"v1":73,"bCoef":0.1,"curve":179.94773754738,"curveF":0.0004560759683152962,"cMask":[],"color":"F8F8F8"},{"v0":73,"v1":72,"bCoef":0.1,"curve":179.98221351296,"curveF":0.0001552163818523414,"cMask":[],"color":"F8F8F8"},{"v0":74,"v1":75,"bCoef":0.1,"curve":-179.58482727820004,"curveF":-0.003623081332869217,"cMask":[],"color":"F8F8F8"},{"v0":75,"v1":74,"bCoef":0.1,"curve":179.58764458796,"curveF":0.0035984953466450956,"cMask":[],"color":"F8F8F8"},{"v0":76,"v1":77,"bCoef":0.1,"curve":-179.99913353641003,"curveF":-0.0000075613212472121415,"cMask":[],"color":"F8F8F8"},{"v0":77,"v1":76,"bCoef":0.1,"curve":-179.98034013624,"curveF":-0.00017156467823623532,"cMask":[],"color":"F8F8F8"},{"v0":78,"v1":79,"bCoef":0.1,"curve":-179.96467398611003,"curveF":-0.00030827763675859586,"cMask":[],"color":"F8F8F8"},{"v0":79,"v1":78,"bCoef":0.1,"curve":179.99380079,"curveF":0.000054098312814100194,"cMask":[],"color":"F8F8F8"},{"v0":80,"v1":81,"bCoef":0.1,"curve":-179.99555315480004,"curveF":-0.00003880604505256444,"cMask":[],"color":"F8F8F8"},{"v0":81,"v1":80,"bCoef":0.1,"curve":-179.98613220153004,"curveF":-0.00012101937224284073,"cMask":[],"color":"F8F8F8"},{"v0":82,"v1":83,"bCoef":0.1,"curve":-179.94841712437002,"curveF":-0.00045014553909957075,"cMask":[],"color":"F8F8F8"},{"v0":83,"v1":82,"bCoef":0.1,"curve":-179.98787776122,"curveF":-0.00010578649010659523,"cMask":[],"color":"F8F8F8"},{"v0":84,"v1":85,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":86,"v1":87,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":88,"v1":89,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":90,"v1":91,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":92,"v1":93,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":94,"v1":95,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":96,"v1":97,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":98,"v1":99,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":100,"v1":101,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":102,"v1":103,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":104,"v1":105,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":106,"v1":107,"bCoef":0.1,"cMask":[],"color":"F8F8F8"},{"v0":109,"v1":108,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":111,"v1":110,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":112,"v1":113,"bCoef":0,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":114,"v1":115,"bCoef":0,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":116,"v1":117,"bCoef":0,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":118,"v1":119,"bCoef":0,"vis":false,"cMask":["ball"],"color":"FFFFFF"}],"planes":[{"normal":[0,1],"dist":-171,"cMask":["ball"]},{"normal":[0,-1],"dist":-171,"cMask":["ball"]},{"normal":[0,1],"dist":-200,"bCoef":0.2},{"normal":[0,-1],"dist":-200,"bCoef":0.2},{"normal":[1,0],"dist":-420,"bCoef":0.2},{"normal":[-1,0],"dist":-420,"bCoef":0.2}],"goals":[{"p0":[-374.25,-62.053454903872],"p1":[-374.25,64.043361696331],"team":"red"},{"p0":[374.25,62],"p1":[374.25,-62],"team":"blue"}],"discs":[{"radius":6.25,"bCoef":0.4,"invMass":1.5,"color":"FFCC00","cGroup":["ball","kick","score"]},{"pos":[-368.53340356886,64.043361696331],"radius":3.9405255187564,"bCoef":1,"invMass":0,"color":"6666CC"},{"pos":[-368.53340356886,-62.053454903872],"radius":3.9405255187564,"bCoef":1,"invMass":0,"color":"6666CC"},{"pos":[368.9681846993,-62.144998272018],"radius":3.9405255187564,"bCoef":1,"invMass":0,"color":"6666CC"},{"pos":[368.09926357786,63.94882446641],"radius":3.9405255187564,"bCoef":1,"invMass":0,"color":"6666CC"},{"pos":[-368,-171],"radius":3,"bCoef":0.1,"invMass":0,"color":"FFCC00","cMask":[]},{"pos":[-368,171],"radius":3,"bCoef":0.1,"invMass":0,"color":"FFCC00","cMask":[]},{"pos":[368,171],"radius":3,"bCoef":0.1,"invMass":0,"color":"FFCC00","cMask":[]},{"pos":[368,-171],"radius":3,"bCoef":0.1,"invMass":0,"color":"FFCC00","cMask":[]}],"playerPhysics":{"bCoef":0,"acceleration":0.11,"kickingAcceleration":0.083},"ballPhysics":"disc0","spawnDistance":180}';
var classicMap = '{"name":"Futsal 1x1 2x2 from HaxMaps","width":420,"height":200,"bg":{"type":"hockey","width":368,"height":171,"kickOffRadius":65},"vertexes":[{"x":-368,"y":171,"cMask":["ball"]},{"x":-368,"y":65,"cMask":["ball"]},{"x":-368,"y":-65,"cMask":["ball"]},{"x":-368,"y":-171,"cMask":["ball"]},{"x":368,"y":171,"cMask":["ball"]},{"x":368,"y":65,"cMask":["ball"]},{"x":368,"y":-65,"cMask":["ball"]},{"x":368,"y":-171,"cMask":["ball"]},{"x":0,"y":65,"bCoef":0.1,"cMask":["red","blue"],"cGroup":["redKO","blueKO"]},{"x":0,"y":-65,"bCoef":0,"cMask":[]},{"x":-384,"y":-65,"bCoef":0.1,"cMask":["ball"]},{"x":384,"y":-65,"bCoef":0.1,"cMask":["ball"]},{"x":-384,"y":65,"bCoef":0.1,"cMask":["ball"]},{"x":384,"y":65,"bCoef":0.1,"cMask":["ball"]},{"x":368,"y":171,"cMask":["ball"]},{"x":368,"y":-171,"cMask":["ball"]},{"x":0,"y":171,"bCoef":0,"cMask":[]},{"x":0,"y":-171,"bCoef":0,"cMask":[]},{"x":0,"y":65,"bCoef":0.1,"cMask":["red","blue"],"cGroup":["redKO","blueKO"]},{"x":0,"y":-65,"bCoef":0.1,"cMask":["red","blue"],"cGroup":["redKO","blueKO"]},{"x":377,"y":-65,"cMask":["ball"]},{"x":377,"y":-171,"cMask":["ball"]},{"x":-377,"y":-65,"cMask":["ball"]},{"x":-377,"y":-171,"cMask":["ball"]},{"x":-377,"y":65,"cMask":["ball"]},{"x":-377,"y":171,"cMask":["ball"]},{"x":377,"y":65,"cMask":["ball"]},{"x":377,"y":171,"cMask":["ball"]},{"x":0,"y":199,"bCoef":0.1,"cMask":["red","blue"],"cGroup":["redKO","blueKO"]},{"x":0,"y":65,"bCoef":0.1,"cMask":["red","blue"],"cGroup":["redKO","blueKO"]},{"x":0,"y":-65,"bCoef":0.1,"cMask":["red","blue"],"cGroup":["redKO","blueKO"]},{"x":0,"y":-199,"bCoef":0.1,"cMask":["red","blue"],"cGroup":["redKO","blueKO"]}],"segments":[{"v0":0,"v1":1,"vis":false,"cMask":["ball"]},{"v0":2,"v1":3,"vis":false,"cMask":["ball"]},{"v0":4,"v1":5,"vis":false,"cMask":["ball"]},{"v0":6,"v1":7,"vis":false,"cMask":["ball"]},{"v0":8,"v1":9,"bCoef":0.1,"curve":180,"curveF":6.123233995736766e-17,"vis":false,"cMask":["red","blue"],"cGroup":["blueKO"]},{"v0":9,"v1":8,"bCoef":0.1,"curve":180,"curveF":6.123233995736766e-17,"vis":false,"cMask":["red","blue"],"cGroup":["redKO"]},{"v0":10,"v1":2,"bCoef":0.1,"curve":35,"curveF":3.1715948023632126,"color":"FFFFFF"},{"v0":6,"v1":11,"bCoef":0.1,"curve":35,"curveF":3.1715948023632126,"color":"FFFFFF"},{"v0":1,"v1":12,"bCoef":0.1,"curve":35,"curveF":3.1715948023632126,"color":"FFFFFF"},{"v0":13,"v1":5,"bCoef":0.1,"curve":35,"curveF":3.1715948023632126,"color":"FFFFFF"},{"v0":12,"v1":10,"bCoef":0.1,"curve":35,"curveF":3.1715948023632126,"cMask":["ball"],"color":"FFFFFF"},{"v0":11,"v1":13,"bCoef":0.1,"curve":35,"curveF":3.1715948023632126,"cMask":["ball"],"color":"FFFFFF"},{"v0":1,"v1":0,"cMask":["ball"],"color":"FFFFFF"},{"v0":5,"v1":4,"cMask":["ball"],"color":"FFFFFF"},{"v0":2,"v1":3,"cMask":["ball"],"color":"FFFFFF"},{"v0":6,"v1":7,"cMask":["ball"],"color":"FFFFFF"},{"v0":0,"v1":14,"cMask":["ball"],"color":"FFFFFF"},{"v0":3,"v1":15,"cMask":["ball"],"color":"FFFFFF"},{"v0":16,"v1":17,"bCoef":0,"cMask":[],"color":"FFFFFF"},{"v0":8,"v1":9,"bCoef":0,"curve":180,"curveF":6.123233995736766e-17,"cMask":[],"color":"FFFFFF"},{"v0":19,"v1":18,"bCoef":0,"curve":180,"curveF":6.123233995736766e-17,"cMask":[],"color":"FFFFFF"},{"v0":2,"v1":1,"bCoef":0,"cMask":[],"color":"FFFFFF"},{"v0":6,"v1":5,"bCoef":0,"cMask":[],"color":"FFFFFF"},{"v0":20,"v1":21,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":22,"v1":23,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":24,"v1":25,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":26,"v1":27,"vis":false,"cMask":["ball"],"color":"FFFFFF"},{"v0":28,"v1":29,"bCoef":0.1,"vis":false,"cMask":["red","blue"],"cGroup":["redKO","blueKO"]},{"v0":30,"v1":31,"bCoef":0.1,"vis":false,"cMask":["red","blue"],"cGroup":["redKO","blueKO"]}],"planes":[{"normal":[0,1],"dist":-171,"cMask":["ball"]},{"normal":[0,-1],"dist":-171,"cMask":["ball"]},{"normal":[0,1],"dist":-200,"bCoef":0.2},{"normal":[0,-1],"dist":-200,"bCoef":0.2},{"normal":[1,0],"dist":-420,"bCoef":0.2},{"normal":[-1,0],"dist":-420,"bCoef":0.2}],"goals":[{"p0":[-377,-65],"p1":[-377,65],"team":"red"},{"p0":[377,65],"p1":[377,-65],"team":"blue"}],"discs":[{"radius":6.4,"color":"EAFF00","cGroup":["ball","kick","score"]},{"pos":[-368,65],"radius":5,"bCoef":1,"invMass":0},{"pos":[-368,-65],"radius":5,"bCoef":1,"invMass":0},{"pos":[368,65],"radius":5,"bCoef":1,"invMass":0},{"pos":[368,-65],"radius":5,"bCoef":1,"invMass":0}],"playerPhysics":{"acceleration":0.11,"kickingAcceleration":0.1,"kickStrength":7},"ballPhysics":"disc0","spawnDistance":180}'; 
var bigMap = '{

	"name" : "Front Liga 3v3",

	"width" : 755,

	"height" : 339,

	"bg" : { "type" : "", "kickOffRadius" : 80, "color" : "414543" },

	"vertexes" : [
		/* 0 */ { "x" : -665, "y" : 290, "cMask" : ["ball" ] },
		/* 1 */ { "x" : -665, "y" : 80, "cMask" : ["ball" ] },
		/* 2 */ { "x" : -665, "y" : -80, "cMask" : ["ball" ] },
		/* 3 */ { "x" : -665, "y" : -290, "cMask" : ["ball" ] },
		/* 4 */ { "x" : 665, "y" : 290, "cMask" : ["ball" ] },
		/* 5 */ { "x" : 665, "y" : 80, "cMask" : ["ball" ] },
		/* 6 */ { "x" : 665, "y" : -80, "cMask" : ["ball" ] },
		/* 7 */ { "x" : 665, "y" : -290, "cMask" : ["ball" ] },
		/* 8 */ { "x" : 0, "y" : 306, "bCoef" : 0.1, "cMask" : ["red","blue" ], "cGroup" : ["redKO","blueKO" ] },
		/* 9 */ { "x" : 0, "y" : 80, "bCoef" : 0.1, "cMask" : ["red","blue" ], "cGroup" : ["redKO","blueKO" ] },
		/* 10 */ { "x" : 0, "y" : -80, "bCoef" : 0, "cMask" : [ ] },
		/* 11 */ { "x" : 0, "y" : -339, "bCoef" : 0.1, "cMask" : ["red","blue" ], "cGroup" : ["redKO","blueKO" ] },
		/* 12 */ { "x" : -693, "y" : -80, "bCoef" : 0.1, "cMask" : ["ball" ] },
		/* 13 */ { "x" : 693, "y" : -80, "bCoef" : 0.1, "cMask" : ["ball" ] },
		/* 14 */ { "x" : -693, "y" : 80, "bCoef" : 0.1, "cMask" : ["ball" ] },
		/* 15 */ { "x" : 693, "y" : 80, "bCoef" : 0.1, "cMask" : ["ball" ] },
		/* 16 */ { "x" : -665, "y" : -215, "bCoef" : 0, "cMask" : [ ] },
		/* 17 */ { "x" : -500, "y" : -50, "bCoef" : 0, "cMask" : [ ] },
		/* 18 */ { "x" : 665, "y" : -215, "bCoef" : 0, "cMask" : [ ] },
		/* 19 */ { "x" : 500, "y" : -50, "bCoef" : 0, "cMask" : [ ] },
		/* 20 */ { "x" : -665, "y" : 215, "bCoef" : 0, "cMask" : [ ] },
		/* 21 */ { "x" : -500, "y" : 50, "bCoef" : 0, "cMask" : [ ] },
		/* 22 */ { "x" : 665, "y" : 215, "bCoef" : 0, "cMask" : [ ] },
		/* 23 */ { "x" : 500, "y" : 50, "bCoef" : 0, "cMask" : [ ] },
		/* 24 */ { "x" : 665, "y" : 290, "cMask" : ["ball" ] },
		/* 25 */ { "x" : 665, "y" : -290, "cMask" : ["ball" ] },
		/* 26 */ { "x" : 0, "y" : 290, "bCoef" : 0, "cMask" : [ ] },
		/* 27 */ { "x" : 0, "y" : -290, "bCoef" : 0, "cMask" : [ ] },
		/* 28 */ { "x" : 0, "y" : 80, "bCoef" : 0.1, "cMask" : ["red","blue" ], "cGroup" : ["redKO","blueKO" ] },
		/* 29 */ { "x" : 0, "y" : -80, "bCoef" : 0.1, "cMask" : ["red","blue" ], "cGroup" : ["redKO","blueKO" ] },
		/* 30 */ { "x" : 674, "y" : -80, "cMask" : ["ball" ] },
		/* 31 */ { "x" : 674, "y" : -290, "cMask" : ["ball" ] },
		/* 32 */ { "x" : -674, "y" : -80, "cMask" : ["ball" ] },
		/* 33 */ { "x" : -674, "y" : -290, "cMask" : ["ball" ] },
		/* 34 */ { "x" : -674, "y" : 80, "cMask" : ["ball" ] },
		/* 35 */ { "x" : -674, "y" : 290, "cMask" : ["ball" ] },
		/* 36 */ { "x" : 674, "y" : 80, "cMask" : ["ball" ] },
		/* 37 */ { "x" : 674, "y" : 290, "cMask" : ["ball" ] },
		/* 38 */ { "x" : 0, "y" : 355, "bCoef" : 0.1, "cMask" : ["red","blue" ], "cGroup" : ["redKO","blueKO" ] },
		/* 39 */ { "x" : 0, "y" : 307, "bCoef" : 0.1, "cMask" : ["red","blue" ], "cGroup" : ["redKO","blueKO" ] }

	],

	"segments" : [
		{ "v0" : 0, "v1" : 1, "vis" : false, "cMask" : ["ball" ] },
		{ "v0" : 2, "v1" : 3, "vis" : false, "cMask" : ["ball" ] },
		{ "v0" : 4, "v1" : 5, "vis" : false, "cMask" : ["ball" ] },
		{ "v0" : 6, "v1" : 7, "vis" : false, "cMask" : ["ball" ] },
		{ "v0" : 8, "v1" : 9, "bCoef" : 0.1, "vis" : false, "cMask" : ["red","blue" ], "cGroup" : ["redKO","blueKO" ] },
		{ "v0" : 9, "v1" : 10, "bCoef" : 0.1, "curve" : 180, "curveF" : 6.123233995736766e-17, "vis" : false, "cMask" : ["red","blue" ], "cGroup" : ["blueKO" ] },
		{ "v0" : 10, "v1" : 9, "bCoef" : 0.1, "curve" : 180, "curveF" : 6.123233995736766e-17, "vis" : false, "cMask" : ["red","blue" ], "cGroup" : ["redKO" ] },
		{ "v0" : 10, "v1" : 11, "bCoef" : 0.1, "vis" : false, "cMask" : ["red","blue" ], "cGroup" : ["redKO","blueKO" ] },
		{ "v0" : 12, "v1" : 2, "bCoef" : 0.1, "curve" : 35, "curveF" : 3.1715948023632126, "cMask" : ["ball" ], "color" : "E02A2A" },
		{ "v0" : 6, "v1" : 13, "bCoef" : 0.1, "curve" : 35, "curveF" : 3.1715948023632126, "cMask" : ["ball" ], "color" : "3E17FF" },
		{ "v0" : 1, "v1" : 14, "bCoef" : 0.1, "curve" : 35, "curveF" : 3.1715948023632126, "cMask" : ["ball" ], "color" : "E02A2A" },
		{ "v0" : 15, "v1" : 5, "bCoef" : 0.1, "curve" : 35, "curveF" : 3.1715948023632126, "cMask" : ["ball" ], "color" : "3E17FF" },
		{ "v0" : 14, "v1" : 12, "bCoef" : 0.1, "curve" : 35, "curveF" : 3.1715948023632126, "cMask" : ["ball" ], "color" : "E02A2A" },
		{ "v0" : 13, "v1" : 15, "bCoef" : 0.1, "curve" : 35, "curveF" : 3.1715948023632126, "cMask" : ["ball" ], "color" : "3E17FF" },
		{ "v0" : 16, "v1" : 17, "bCoef" : 0, "curve" : 89.99999999999999, "curveF" : 1.0000000000000002, "cMask" : [ ], "color" : "E02A2A" },
		{ "v0" : 19, "v1" : 18, "bCoef" : 0, "curve" : 89.99999999999999, "curveF" : 1.0000000000000002, "cMask" : [ ], "color" : "3E17FF" },
		{ "v0" : 21, "v1" : 20, "bCoef" : 0, "curve" : 89.99999999999999, "curveF" : 1.0000000000000002, "cMask" : [ ], "color" : "E02A2A" },
		{ "v0" : 22, "v1" : 23, "bCoef" : 0, "curve" : 89.99999999999999, "curveF" : 1.0000000000000002, "cMask" : [ ], "color" : "3E17FF" },
		{ "v0" : 17, "v1" : 21, "bCoef" : 0, "cMask" : [ ], "color" : "E02A2A" },
		{ "v0" : 19, "v1" : 23, "bCoef" : 0, "cMask" : [ ], "color" : "3E17FF" },
		{ "v0" : 1, "v1" : 0, "cMask" : ["ball" ], "color" : "FFFFFF" },
		{ "v0" : 5, "v1" : 4, "cMask" : ["ball" ], "color" : "FFFFFF" },
		{ "v0" : 2, "v1" : 3, "cMask" : ["ball" ], "color" : "FFFFFF" },
		{ "v0" : 6, "v1" : 7, "cMask" : ["ball" ], "color" : "FFFFFF" },
		{ "v0" : 0, "v1" : 24, "cMask" : ["ball" ], "color" : "FFFFFF" },
		{ "v0" : 3, "v1" : 25, "cMask" : ["ball" ], "color" : "FFFFFF" },
		{ "v0" : 26, "v1" : 27, "bCoef" : 0, "cMask" : [ ], "color" : "FFFFFF" },
		{ "v0" : 9, "v1" : 10, "bCoef" : 0, "curve" : 180, "curveF" : 6.123233995736766e-17, "cMask" : [ ], "color" : "FFFFFF" },
		{ "v0" : 29, "v1" : 28, "bCoef" : 0, "curve" : 180, "curveF" : 6.123233995736766e-17, "cMask" : [ ], "color" : "FFFFFF" },
		{ "v0" : 2, "v1" : 1, "bCoef" : 0, "cMask" : [ ], "color" : "FFFFFF" },
		{ "v0" : 6, "v1" : 5, "bCoef" : 0, "cMask" : [ ], "color" : "FFFFFF" },
		{ "v0" : 30, "v1" : 31, "vis" : false, "cMask" : ["ball" ], "color" : "FFFFFF" },
		{ "v0" : 32, "v1" : 33, "vis" : false, "cMask" : ["ball" ], "color" : "FFFFFF" },
		{ "v0" : 34, "v1" : 35, "vis" : false, "cMask" : ["ball" ], "color" : "FFFFFF" },
		{ "v0" : 36, "v1" : 37, "vis" : false, "cMask" : ["ball" ], "color" : "FFFFFF" },
		{ "v0" : 38, "v1" : 39, "bCoef" : 0.1, "vis" : false, "cMask" : ["red","blue" ], "cGroup" : ["redKO","blueKO" ] }

	],

	"planes" : [
		{ "normal" : [0,1 ], "dist" : -290, "cMask" : ["ball" ] },
		{ "normal" : [0,-1 ], "dist" : -290, "cMask" : ["ball" ] },
		{ "normal" : [0,1 ], "dist" : -339, "bCoef" : 0.2 },
		{ "normal" : [0,-1 ], "dist" : -339, "bCoef" : 0.2 },
		{ "normal" : [1,0 ], "dist" : -755, "bCoef" : 0.2 },
		{ "normal" : [-1,0 ], "dist" : -755, "bCoef" : 0.2 }

	],

	"goals" : [
		{ "p0" : [-674,-80 ], "p1" : [-674,80 ], "team" : "red" },
		{ "p0" : [674,80 ], "p1" : [674,-80 ], "team" : "blue" }

	],

	"discs" : [
		{ "radius" : 6.2, "color" : "FFF40D", "cGroup" : ["ball","kick","score" ] },
		{ "pos" : [-665,80 ], "radius" : 5, "bCoef" : 1, "invMass" : 0, "_selected" : true, "color" : "E02A2A" },
		{ "pos" : [-665,-80 ], "radius" : 5, "bCoef" : 1, "invMass" : 0, "color" : "E02A2A" },
		{ "pos" : [665,80 ], "radius" : 5, "bCoef" : 1, "invMass" : 0, "color" : "3E17FF" },
		{ "pos" : [665,-80 ], "radius" : 5, "bCoef" : 1, "invMass" : 0, "color" : "3E17FF" }

	],

	"playerPhysics" : {
		"acceleration" : 0.11,
		"kickingAcceleration" : 0.1,
		"kickStrength" : 7.5

	},

	"ballPhysics" : "disc0",

	"spawnDistance" : 310,

	"traits" : {
		

	}';

/* OPTIONS */

var afkLimit = 12;
var drawTimeLimit = Infinity;
var maxTeamSize = 4; // This works for 1 (you might want to adapt things to remove some useless stats in 1v1 like assist or cs), 2, 3 or 4
var slowMode = 0;

/* PLAYERS */

const Team = { SPECTATORS: 0, RED: 1, BLUE: 2 };
var extendedP = [];
const eP = { ID: 0, AUTH: 1, CONN: 2, AFK: 3, ACT: 4, GK: 5, MUTE: 6 };
const Ss = { GA: 0, WI: 1, DR: 2, LS: 3, WR: 4, GL: 5, AS: 6, GK: 7, CS: 8, CP: 9, RL: 10, NK: 11}
var players;
var teamR;
var teamB;
var teamS;

/* GAME */

var lastTeamTouched;
var lastPlayersTouched; // These allow to get good goal notifications (it should be lastPlayersKicked, waiting on a next update to get better track of shots on target)
var countAFK = false; // Created to get better track of activity
var activePlay = false; // Created to get better track of the possession
var goldenGoal = false;
var SMSet = new Set(); // Set created to get slow mode which is useful in chooseMode
var banList = []; // Getting track of the bans, so we can unban ppl if we want

/* STATS */

var game;
var GKList = ["",""];
var Rposs = 0;
var Bposs = 0;
var point = [{"x": 0, "y": 0}, {"x": 0, "y": 0}]; // created to get ball speed
var ballSpeed;
var lastWinner = Team.SPECTATORS;
var streak = 0;
var allBlues = []; // This is to count the players who should be counted for the stats. This includes players who left after the game has started, doesn't include those who came too late or ...
var allReds = []; // ... those who came in a very unequal game.

/* BALANCE & CHOOSE */

var inChooseMode = false; // This variable enables to distinguish the 2 phases of playing and choosing which should be dealt with very differently
var redCaptainChoice = "";
var blueCaptainChoice = "";
var chooseTime = 20;
var timeOutCap;

/* AUXILIARY */

var checkTimeVariable = false; // This is created so the chat doesn't get spammed when a game is ending via timeLimit
var statNumber = 0; // This allows the room to be given stat information every X minutes
var endGameVariable = false; // This variable with the one below helps distinguish the cases where games are stopped because they have finished to the ones where games are stopped due to player movements or resetting teams
var resettingTeams = false;
var capLeft = false;
var statInterval = 6;

loadMap(aloneMap, 0, 0);

/* OBJECTS */

function Goal(time, team, striker, assist) {
	this.time = time;
	this.team = team;
	this.striker = striker;
	this.assist = assist;
}

function Game(date, scores, goals) {
	this.date = date;
	this.scores = scores;
	this.goals = goals;
}

/* FUNCTIONS */

/* AUXILIARY FUNCTIONS */

function getRandomInt(max) { // returns a random number from 0 to max-1
	return Math.floor(Math.random() * Math.floor(max)); 
}

function getTime(scores) { // returns the current time of the game
	return "[" + Math.floor(Math.floor(scores.time/60)/10).toString() + Math.floor(Math.floor(scores.time/60)%10).toString() + ":" + Math.floor(Math.floor(scores.time - (Math.floor(scores.time/60) * 60))/10).toString() + Math.floor(Math.floor(scores.time - (Math.floor(scores.time/60) * 60))%10).toString() + "]"
}

function pointDistance(p1, p2) {
	var d1 = p1.x - p2.x;
	var d2 = p1.y - p2.y;
	return Math.sqrt(d1 * d1 + d2 * d2);
}

/* BUTTONS */

function topBtn() {
	if (teamS.length == 0) {
		return;
	}
	else {
		if (teamR.length == teamB.length) {
			if (teamS.length > 1) {
				room.setPlayerTeam(teamS[0].id, Team.RED);
				room.setPlayerTeam(teamS[1].id, Team.BLUE);
			}
			return;
		}
		else if (teamR.length < teamB.length) {
			room.setPlayerTeam(teamS[0].id, Team.RED);
		}
		else {
			room.setPlayerTeam(teamS[0].id, Team.BLUE);
		}
	}
}

function randomBtn() {
	if (teamS.length == 0) {
		return;
	}
	else {
		if (teamR.length == teamB.length) {
			if (teamS.length > 1) {
				var r = getRandomInt(teamS.length);
				room.setPlayerTeam(teamS[r].id, Team.RED);
				teamS = teamS.filter((spec) => spec.id != teamS[r].id);
				room.setPlayerTeam(teamS[getRandomInt(teamS.length)].id, Team.BLUE);
			}
			return;
		}
		else if (teamR.length < teamB.length) {
			room.setPlayerTeam(teamS[getRandomInt(teamS.length)].id, Team.RED);
		}
		else {
			room.setPlayerTeam(teamS[getRandomInt(teamS.length)].id, Team.BLUE);
		}
	}
}

function blueToSpecBtn() {
	resettingTeams = true;
	setTimeout(() => { resettingTeams = false; }, 100);
	for (var i = 0; i < teamB.length; i++) {
		room.setPlayerTeam(teamB[teamB.length - 1 - i].id, Team.SPECTATORS);
	}
}

function redToSpecBtn() {
	resettingTeams = true;
	setTimeout(() => { resettingTeams = false; }, 100);
	for (var i = 0; i < teamR.length; i++) {
		room.setPlayerTeam(teamR[teamR.length - 1 - i].id, Team.SPECTATORS);
	}
}

function resetBtn() {
	resettingTeams = true;
	setTimeout(() => { resettingTeams = false; }, 100);
	if (teamR.length <= teamB.length) {
		for (var i = 0; i < teamR.length; i++) {
			room.setPlayerTeam(teamB[teamB.length - 1 - i].id, Team.SPECTATORS);
			room.setPlayerTeam(teamR[teamR.length - 1 - i].id, Team.SPECTATORS);
		}
		for (var i = teamR.length; i < teamB.length; i++) {
			room.setPlayerTeam(teamB[teamB.length - 1 - i].id, Team.SPECTATORS);
		}
	}
	else {
		for (var i = 0; i < teamB.length; i++) {
			room.setPlayerTeam(teamB[teamB.length - 1 - i].id, Team.SPECTATORS);
			room.setPlayerTeam(teamR[teamR.length - 1 - i].id, Team.SPECTATORS);
		}
		for (var i = teamB.length; i < teamR.length; i++) {
			room.setPlayerTeam(teamR[teamR.length - 1 - i].id, Team.SPECTATORS);
		}
	}
}

function blueToRedBtn() {
	resettingTeams = true;
	setTimeout(() => { resettingTeams = false; }, 100);
	for (var i = 0; i < teamB.length; i++) {
		room.setPlayerTeam(teamB[i].id, Team.RED);
	}
}

/* GAME FUNCTIONS */

function checkTime() {
	const scores = room.getScores();
	game.scores = scores;
	if (Math.abs(scores.time - scores.timeLimit) <= 0.01 && scores.timeLimit != 0) {
		if (scores.red != scores.blue) {
			if (checkTimeVariable == false) {
				checkTimeVariable = true;
				setTimeout(() => { checkTimeVariable = false; }, 3000);
				scores.red > scores.blue ? endGame(Team.RED) : endGame(Team.BLUE);
				setTimeout(() => { room.stopGame(); }, 2000);
			}
			return;
		}
		goldenGoal = true;
		room.sendChat("⚽ First goal wins !");
	}
	if (Math.abs(drawTimeLimit * 60 - scores.time - 60) <= 0.01 && players.length > 2) {
		if (checkTimeVariable == false) {
			checkTimeVariable = true;
			setTimeout(() => { checkTimeVariable = false; }, 10);
			room.sendChat("⌛ 60 seconds left until draw !");
		}
	}
	if (Math.abs(scores.time - drawTimeLimit * 60) <= 0.01 && players.length > 2) {
		if (checkTimeVariable == false) {
			checkTimeVariable = true;
			setTimeout(() => { checkTimeVariable = false; }, 10);
			endGame(Team.SPECTATORS);
			room.stopGame();
			goldenGoal = false;
		}
	}
}

function endGame(winner) { // handles the end of a game : no stopGame function inside
	players.length >= 2 * maxTeamSize - 1 ? activateChooseMode() : null;
	const scores = room.getScores();
	game.scores = scores;
	Rposs = Rposs/(Rposs+Bposs);
	Bposs = 1 - Rposs;
	lastWinner = winner;
	endGameVariable = true;
	if (winner == Team.RED) {
		streak++;
		room.sendChat("🔴 Red Team won " + scores.red + "-" + scores.blue + " ! Current streak : " + streak + " 🏆");
	}
	else if (winner == Team.BLUE) {
		streak = 1;
		room.sendChat("🔵 Blue Team won " + scores.blue + "-" + scores.red + " ! Current streak : " + streak + " 🏆");
	}
	else {
		streak = 0;
		room.sendChat("💤 Draw limit reached! 💤");
    }
    room.sendChat("⭐ Possession : 🔴 " + (Rposs*100).toPrecision(3).toString() + "% : " + (Bposs*100).toPrecision(3).toString() + "% 🔵");
    scores.red == 0 ? (scores.blue == 0 ? room.sendChat("🏆 " + GKList[0].name + " and " + GKList[1].name + " kept a CS ! ") : room.sendChat("🏆 " + GKList[1].name + " kept a CS ! ")) : scores.blue == 0 ? room.sendChat("🏆 " + GKList[0].name + " kept a CS ! ") : null;
	updateStats();
}

function quickRestart() {
	room.stopGame();
	setTimeout(() => { room.startGame(); }, 2000);
}

function resumeGame() {
	setTimeout(() => { room.startGame(); }, 2000);
	setTimeout(() => { room.pauseGame(false); }, 1000);
}

function activateChooseMode() {
	inChooseMode = true;
	slowMode = 2;
	room.sendChat("2 seconds slow mode enabled !");
}

function deactivateChooseMode() {
	inChooseMode = false;
	clearTimeout(timeOutCap);
	if (slowMode != 0) {
		slowMode = 0;
		room.sendChat("Slow mode terminated.");
	}
	redCaptainChoice = "";
	blueCaptainChoice = "";
}

function loadMap(map, scoreLim, timeLim) {
	if (map == aloneMap) {
		room.setCustomStadium(aloneMap);
	}
	else if (map == classicMap) {
		(classicMap != '') ? room.setCustomStadium(classicMap) : room.setDefaultStadium("Classic");
	}
	else if (map == bigMap) {
		(bigMap != '.') ? room.setCustomStadium(bigMap) : room.setDefaultStadium("Big");
	}
	else {
		room.setCustomStadium(map);
	}
	room.setScoreLimit(scoreLim);
	room.setTimeLimit(timeLim);
}

/* PLAYER FUNCTIONS */

function updateTeams() { // update the players' list and all the teams' list
	players = room.getPlayerList().filter((player) => player.id != 0 && !getAFK(player));
	teamR = players.filter(p => p.team === Team.RED);
	teamB = players.filter(p => p.team === Team.BLUE);
	teamS = players.filter(p => p.team === Team.SPECTATORS);
}

function getAuth(player) {
	return extendedP.filter((a) => a[0] == player.id) != null ? extendedP.filter((a) => a[0] == player.id)[0][eP.AUTH] : null;
}

function getAFK(player) {
	return extendedP.filter((a) => a[0] == player.id) != null ? extendedP.filter((a) => a[0] == player.id)[0][eP.AFK] : null;
}

function setAFK(player, value) {
	extendedP.filter((a) => a[0] == player.id).forEach((player) => player[eP.AFK] = value);
}

function getActivity(player) {
	return extendedP.filter((a) => a[0] == player.id) != null ? extendedP.filter((a) => a[0] == player.id)[0][eP.ACT] : null;
}

function setActivity(player, value) {
	extendedP.filter((a) => a[0] == player.id).forEach((player) => player[eP.ACT] = value);
}

function getGK(player) {
	return extendedP.filter((a) => a[0] == player.id) != null ? extendedP.filter((a) => a[0] == player.id)[0][eP.GK] : null;
}

function setGK(player, value) {
	extendedP.filter((a) => a[0] == player.id).forEach((player) => player[eP.GK] = value);
}

function getMute(player) {
	return extendedP.filter((a) => a[0] == player.id) != null ? extendedP.filter((a) => a[0] == player.id)[0][eP.MUTE] : null;
}

function setMute(player, value) {
	extendedP.filter((a) => a[0] == player.id).forEach((player) => player[eP.MUTE] = value);
}

/* BALANCE & CHOOSE FUNCTIONS */

function updateRoleOnPlayerIn() {
	updateTeams();
	if (inChooseMode) {
		if (players.length == 6) {
			loadMap(bigMap, scoreLimitBig, timeLimitBig);
		}
		getSpecList(teamR.length <= teamB.length ? teamR[0] : teamB[0]);
	}
	balanceTeams();
}

function updateRoleOnPlayerOut() {
    updateTeams();
	if (room.getScores() != null) {
		var scores = room.getScores();
		if (players.length >= 2 * maxTeamSize && scores.time >= (5/6) * game.scores.timeLimit && teamR.length != teamB.length) {
			if (teamR.length < teamB.length) {
				if (scores.blue - scores.red == 2) {
					endGame(Team.BLUE);
					room.sendChat("🤖 Ragequit detected. Game ended 🤖");
					setTimeout(() => { room.stopGame(); }, 100);
					return;
				}
			}
			else {
				if (scores.red - scores.blue == 2) {
					endGame(Team.RED);
					room.sendChat("🤖 Ragequit detected. Game ended 🤖");
					setTimeout(() => { room.stopGame(); }, 100);
					return;
				}
			}
		}
	}
	if (inChooseMode) {
		if (players.length == 5) {
			loadMap(classicMap, scoreLimitClassic, timeLimitClassic);
		}
		if (teamR.length == 0 || teamB.length == 0) {
			teamR.length == 0 ? room.setPlayerTeam(teamS[0].id, Team.RED) : room.setPlayerTeam(teamS[0].id, Team.BLUE);
			return;
		}
		if (Math.abs(teamR.length - teamB.length) == teamS.length) {
			room.sendChat("🤖 No choices left, let me handle this situation... 🤖");
			deactivateChooseMode();
			resumeGame();
			var b = teamS.length;
			if (teamR.length > teamB.length) {
				for (var i = 0 ; i < b ; i++) {
					setTimeout(() => { room.setPlayerTeam(teamS[0].id, Team.BLUE); }, 5*i);
				}
			}
			else {
				for (var i = 0 ; i < b ; i++) {
					setTimeout(() => { room.setPlayerTeam(teamS[0].id, Team.RED); }, 5*i);
				}
			}
			return;
		}
		if (streak == 0 && room.getScores() == null) {
			if (Math.abs(teamR.length - teamB.length) == 2) { // if someone left a team has 2 more players than the other one, put the last chosen guy back in his place so it's fair
				room.sendChat("🤖 Balancing teams... 🤖");
				teamR.length > teamB.length ? room.setPlayerTeam(teamR[teamR.length - 1].id, Team.SPECTATORS) : room.setPlayerTeam(teamB[teamB.length - 1].id, Team.SPECTATORS);
			}
		}
		if (teamR.length == teamB.length && teamS.length < 2) {
			deactivateChooseMode();
			resumeGame();
			return;
		}
		capLeft ? choosePlayer() : getSpecList(teamR.length <= teamB.length ? teamR[0] : teamB[0]);
	}
	balanceTeams();
}

function balanceTeams() {
	if (!inChooseMode) {
		if (players.length == 1 && teamR.length == 0) {
            quickRestart();
            loadMap(aloneMap, 0, 0);
			room.setPlayerTeam(players[0].id, Team.RED);
		}
		else if (Math.abs(teamR.length - teamB.length) == teamS.length && teamS.length > 0) {
			const n = Math.abs(teamR.length - teamB.length);
			if (players.length == 2) {
				quickRestart();
				loadMap(classicMap, scoreLimitClassic, timeLimitClassic);
			}
			if (teamR.length > teamB.length) {
				for (var i = 0 ; i < n ; i++) {
					room.setPlayerTeam(teamS[i].id, Team.BLUE);
				}
			}
			else {
				for (var i = 0 ; i < n ; i++) {
					room.setPlayerTeam(teamS[i].id, Team.RED);
				}
			}
		}
		else if (Math.abs(teamR.length - teamB.length) > teamS.length) {
			const n = Math.abs(teamR.length - teamB.length);
			if (players.length == 1) {
				quickRestart();
				loadMap(aloneMap, 0, 0);
				room.setPlayerTeam(players[0].id, Team.RED);
				return;
			}
			else if (players.length == 5) {
				quickRestart();
				loadMap(classicMap, scoreLimitClassic, timeLimitClassic);
			}
			if (players.length == maxTeamSize * 2 - 1) {
				allReds = [];
				allBlues = [];
			}
			if (teamR.length > teamB.length) {
				for (var i = 0 ; i < n ; i++) {
					room.setPlayerTeam(teamR[teamR.length - 1 - i].id, Team.SPECTATORS);
				}
			}
			else {
				for (var i = 0 ; i < n ; i++) {
					room.setPlayerTeam(teamB[teamB.length - 1 - i].id, Team.SPECTATORS);
				}
			}
		}
		else if (Math.abs(teamR.length - teamB.length) < teamS.length && teamR.length != teamB.length) {
			room.pauseGame(true);
			activateChooseMode();
			choosePlayer();
		}
		else if (teamS.length >= 2 && teamR.length == teamB.length && teamR.length < maxTeamSize) {
			if (teamR.length == 2) {
				quickRestart();
				loadMap(bigMap, scoreLimitBig, timeLimitBig);
			}
			topBtn();
		}
	}
}

function choosePlayer() {
	clearTimeout(timeOutCap);
	if (teamR.length <= teamB.length && teamR.length != 0) {
		room.sendChat("[PV] To choose a player, enter his number in the list given or use 'top', 'random' or 'bottom'.", teamR[0].id);
		timeOutCap = setTimeout(function (player) { room.sendChat("[PV] Hurry up @" + player.name + ", only " + Number.parseInt(chooseTime / 2) + " seconds left to choose !", player.id); timeOutCap = setTimeout(function (player) { room.kickPlayer(player.id, "You didn't choose in time !", false); }, chooseTime * 500, teamR[0]); }, chooseTime * 1000, teamR[0]);
	}
	else if (teamB.length < teamR.length && teamB.length != 0) {
		room.sendChat("[PV] To choose a player, enter his number in the list given or use 'top', 'random' or 'bottom'.", teamB[0].id);
		timeOutCap = setTimeout(function (player) { room.sendChat("[PV] Hurry up @" + player.name + ", only " + Number.parseInt(chooseTime / 2) + " seconds left to choose !", player.id); timeOutCap = setTimeout(function (player) { room.kickPlayer(player.id, "You didn't choose in time !", false); }, chooseTime * 500, teamB[0]); }, chooseTime * 1000, teamB[0]);
	}
	if (teamR.length != 0 && teamB.length != 0) getSpecList(teamR.length <= teamB.length ? teamR[0] : teamB[0]);
}

function getSpecList(player) {
	var cstm = "[PV] Players : ";
	for (var i = 0 ; i < teamS.length ; i++) {
		if (140 - cstm.length < (teamS[i].name + "[" + (i+1) + "], ").length) {
			room.sendChat(cstm, player.id);
			cstm = "... ";
		}
		cstm += teamS[i].name + "[" + (i+1) + "], ";
	}
	cstm = cstm.substring(0,cstm.length - 2);
	cstm += ".";
	room.sendChat(cstm, player.id);
}

/* STATS FUNCTIONS */

function getLastTouchOfTheBall() {
	const ballPosition = room.getBallPosition();
	updateTeams();
	for (var i = 0; i < players.length; i++) {
		if (players[i].position != null) {
			var distanceToBall = pointDistance(players[i].position, ballPosition);
			if (distanceToBall < triggerDistance) {
				!activePlay ? activePlay = true : null;
				if (lastTeamTouched == players[i].team && lastPlayersTouched[0] != null && lastPlayersTouched[0].id != players[i].id) {
					lastPlayersTouched[1] = lastPlayersTouched[0];
					lastPlayersTouched[0] = players[i];
				}
				lastTeamTouched = players[i].team;
			}
		}
	}
}

function getStats() { // gives possession, ball speed and GK of each team
	if (activePlay) {
		updateTeams();
		lastTeamTouched == Team.RED ? Rposs++ : Bposs++;
		var ballPosition = room.getBallPosition();
		point[1] = point[0];
		point[0] = ballPosition;
		ballSpeed = (pointDistance(point[0], point[1]) * 60 * 60 * 60)/15000;
		var k = [-1, Infinity];
		for (var i = 0; i < teamR.length; i++) {
			if (teamR[i].position.x < k[1]) {
				k[0] = teamR[i];
				k[1] = teamR[i].position.x;
			}
		}
		k[0] != -1 ? setGK(k[0], getGK(k[0]) + 1) : null;
		k = [-1, -Infinity];
		for (var i = 0; i < teamB.length; i++) {
			if (teamB[i].position.x > k[1]) {
				k[0] = teamB[i];
				k[1] = teamB[i].position.x;
			}
		}
		k[0] != -1 ? setGK(k[0], getGK(k[0]) + 1) : null;
		findGK();
	}
}

function updateStats() {
	if (players.length >= 2 * maxTeamSize && (game.scores.time >= (5 / 6) * game.scores.timeLimit || game.scores.red == game.scores.scoreLimit || game.scores.blue == game.scores.scoreLimit) && allReds.length >= maxTeamSize && allBlues.length >= maxTeamSize) {
		var stats;
		for (var i = 0; i < allReds.length; i++) {
			localStorage.getItem(getAuth(allReds[i])) ? stats = JSON.parse(localStorage.getItem(getAuth(allReds[i]))) : stats = [0, 0, 0, 0, "0.00", 0, 0, 0, 0, "0.00", "player", allReds[i].name];
			stats[Ss.GA]++;
			lastWinner == Team.RED ? stats[Ss.WI]++ : lastWinner == Team.BLUE ? stats[Ss.LS]++ : stats[Ss.DR]++;
			stats[Ss.WR] = (100 * stats[Ss.WI] / stats[Ss.GA]).toPrecision(3);
			localStorage.setItem(getAuth(allReds[i]), JSON.stringify(stats));
		}
		for (var i = 0; i < allBlues.length; i++) {
			localStorage.getItem(getAuth(allBlues[i])) ? stats = JSON.parse(localStorage.getItem(getAuth(allBlues[i]))) : stats = [0, 0, 0, 0, "0.00", 0, 0, 0, 0, "0.00", "player", allBlues[i].name];
			stats[Ss.GA]++;
			lastWinner == Team.BLUE ? stats[Ss.WI]++ : lastWinner == Team.RED ? stats[Ss.LS]++ : stats[Ss.DR]++;
			stats[Ss.WR] = (100 * stats[Ss.WI] / stats[Ss.GA]).toPrecision(3);
			localStorage.setItem(getAuth(allBlues[i]), JSON.stringify(stats));
		}
		for (var i = 0; i < game.goals.length; i++) {
			if (game.goals[i].striker != null) {
				if ((allBlues.concat(allReds)).findIndex((player) => player.id == game.goals[i].striker.id) != -1) {
					stats = JSON.parse(localStorage.getItem(getAuth(game.goals[i].striker)));
					stats[Ss.GL]++;
					localStorage.setItem(getAuth(game.goals[i].striker), JSON.stringify(stats));
				}
			}
			if (game.goals[i].assist != null) {
				if ((allBlues.concat(allReds)).findIndex((player) => player.name == game.goals[i].assist.name) != -1) {
					stats = JSON.parse(localStorage.getItem(getAuth(game.goals[i].assist)));
					stats[Ss.AS]++;
					localStorage.setItem(getAuth(game.goals[i].assist), JSON.stringify(stats));
				}
			}
		}
		if (allReds.findIndex((player) => player.id == GKList[0].id) != -1) {
			stats = JSON.parse(localStorage.getItem(getAuth(GKList[0])));
			stats[Ss.GK]++;
			game.scores.blue == 0 ? stats[Ss.CS]++ : null;
			stats[Ss.CP] = (100 * stats[Ss.CS] / stats[Ss.GK]).toPrecision(3);
			localStorage.setItem(getAuth(GKList[0]), JSON.stringify(stats));
		}
		if (allBlues.findIndex((player) => player.id == GKList[1].id) != -1) {
			stats = JSON.parse(localStorage.getItem(getAuth(GKList[1])));
			stats[Ss.GK]++;
			game.scores.red == 0 ? stats[Ss.CS]++ : null;
			stats[Ss.CP] = (100 * stats[Ss.CS] / stats[Ss.GK]).toPrecision(3);
			localStorage.setItem(getAuth(GKList[1]), JSON.stringify(stats));
		}
	}
}

function findGK() {
	var tab = [[-1,""], [-1,""]];
	for (var i = 0; i < extendedP.length ; i++) {
		if (room.getPlayer(extendedP[i][eP.ID]) != null && room.getPlayer(extendedP[i][eP.ID]).team == Team.RED) {
			if (tab[0][0] < extendedP[i][eP.GK]) {
				tab[0][0] = extendedP[i][eP.GK];
				tab[0][1] = room.getPlayer(extendedP[i][eP.ID]);
			}
		}
		else if (room.getPlayer(extendedP[i][eP.ID]) != null && room.getPlayer(extendedP[i][eP.ID]).team == Team.BLUE) {
			if (tab[1][0] < extendedP[i][eP.GK]) {
				tab[1][0] = extendedP[i][eP.GK];
				tab[1][1] = room.getPlayer(extendedP[i][eP.ID]);
			}
		}
	}
	GKList = [tab[0][1], tab[1][1]];
}

setInterval(() => {
	var tableau = [];
	if (statNumber % 5 == 0) {
		Object.keys(localStorage).forEach(function (key) { if (!["player_name", "view_mode", "geo", "avatar", "player_auth_key"].includes(key)) { tableau.push([(JSON.parse(localStorage.getItem(key))[Ss.NK]), (JSON.parse(localStorage.getItem(key))[Ss.GA])]); } });
		if (tableau.length < 5) {
			return false;
		}
		tableau.sort(function (a, b) { return b[1] - a[1]; });
		room.sendChat("Games> #1 " + tableau[0][0] + ": " + tableau[0][1] + " #2 " + tableau[1][0] + ": " + tableau[1][1] + " #3 " + tableau[2][0] + ": " + tableau[2][1] + " #4 " + tableau[3][0] + ": " + tableau[3][1] + " #5 " + tableau[4][0] + ": " + tableau[4][1]);
	}
	if (statNumber % 5 == 1) {
		Object.keys(localStorage).forEach(function (key) { if (!["player_name", "view_mode", "geo", "avatar", "player_auth_key"].includes(key)) { tableau.push([(JSON.parse(localStorage.getItem(key))[Ss.NK]), (JSON.parse(localStorage.getItem(key))[Ss.WI])]); } });
		if (tableau.length < 5) {
			return false;
		}
		tableau.sort(function (a, b) { return b[1] - a[1]; });
		room.sendChat("Wins> #1 " + tableau[0][0] + ": " + tableau[0][1] + " #2 " + tableau[1][0] + ": " + tableau[1][1] + " #3 " + tableau[2][0] + ": " + tableau[2][1] + " #4 " + tableau[3][0] + ": " + tableau[3][1] + " #5 " + tableau[4][0] + ": " + tableau[4][1]);
	}
	if (statNumber % 5 == 2) {
		Object.keys(localStorage).forEach(function (key) { if (!["player_name", "view_mode", "geo", "avatar", "player_auth_key"].includes(key)) { tableau.push([(JSON.parse(localStorage.getItem(key))[Ss.NK]), (JSON.parse(localStorage.getItem(key))[Ss.GL])]); } });
		if (tableau.length < 5) {
			return false;
		}
		tableau.sort(function (a, b) { return b[1] - a[1]; });
		room.sendChat("Goals> #1 " + tableau[0][0] + ": " + tableau[0][1] + " #2 " + tableau[1][0] + ": " + tableau[1][1] + " #3 " + tableau[2][0] + ": " + tableau[2][1] + " #4 " + tableau[3][0] + ": " + tableau[3][1] + " #5 " + tableau[4][0] + ": " + tableau[4][1]);
	}
	if (statNumber % 5 == 3) {
		Object.keys(localStorage).forEach(function (key) { if (!["player_name", "view_mode", "geo", "avatar", "player_auth_key"].includes(key)) { tableau.push([(JSON.parse(localStorage.getItem(key))[Ss.NK]), (JSON.parse(localStorage.getItem(key))[Ss.AS])]); } });
		if (tableau.length < 5) {
			return false;
		}
		tableau.sort(function (a, b) { return b[1] - a[1]; });
		room.sendChat("Assists> #1 " + tableau[0][0] + ": " + tableau[0][1] + " #2 " + tableau[1][0] + ": " + tableau[1][1] + " #3 " + tableau[2][0] + ": " + tableau[2][1] + " #4 " + tableau[3][0] + ": " + tableau[3][1] + " #5 " + tableau[4][0] + ": " + tableau[4][1]);
	}
	if (statNumber % 5 == 4) {
		Object.keys(localStorage).forEach(function (key) { if (!["player_name", "view_mode", "geo", "avatar", "player_auth_key"].includes(key)) { tableau.push([(JSON.parse(localStorage.getItem(key))[Ss.NK]), (JSON.parse(localStorage.getItem(key))[Ss.CS])]); } });
		if (tableau.length < 5) {
			return false;
		}
		tableau.sort(function (a, b) { return b[1] - a[1]; });
		room.sendChat("CS> #1 " + tableau[0][0] + ": " + tableau[0][1] + " #2 " + tableau[1][0] + ": " + tableau[1][1] + " #3 " + tableau[2][0] + ": " + tableau[2][1] + " #4 " + tableau[3][0] + ": " + tableau[3][1] + " #5 " + tableau[4][0] + ": " + tableau[4][1]);
	}
	statNumber++;
}, statInterval * 60 * 1000);

/* EVENTS */

/* PLAYER MOVEMENT */

room.onPlayerJoin = function(player) {
	extendedP.push([player.id, player.auth, player.conn, false, 0, 0, false]);
	updateRoleOnPlayerIn();
	room.sendChat("[PV] 👋 Welcome " + player.name + " ! Type '!help' to see the commands.", player.id);
	if (localStorage.getItem(player.auth) != null) {
		if (JSON.parse(localStorage.getItem(player.auth))[Ss.RL] != "player") {
			room.setPlayerAdmin(player.id, true);
			room.sendChat((JSON.parse(localStorage.getItem(player.auth))[Ss.RL] == "master" ? "Master " : "Admin ") + player.name + " has connected to the room !");
		}
	}
}

room.onPlayerTeamChange = function(changedPlayer, byPlayer) {
	if (changedPlayer.id == 0) {
		room.setPlayerTeam(0, Team.SPECTATORS);
		return;
	}
	if (getAFK(changedPlayer) && changedPlayer.team != Team.SPECTATORS) {
		room.setPlayerTeam(changedPlayer.id, Team.SPECTATORS);
		room.sendChat(changedPlayer.name + " is AFK !");
		return;
	}
	updateTeams();
	if (room.getScores() != null) {
		var scores = room.getScores();
		if (changedPlayer.team != Team.SPECTATORS && scores.time <= (3/4) * scores.timeLimit  && Math.abs(scores.blue - scores.red) < 2) {
			(changedPlayer.team == Team.RED) ? allReds.push(changedPlayer) : allBlues.push(changedPlayer);
		}
	}
	if (changedPlayer.team == Team.SPECTATORS) {
		setActivity(changedPlayer, 0);
	}
	if (inChooseMode && resettingTeams == false && byPlayer.id == 0) {
		if (Math.abs(teamR.length - teamB.length) == teamS.length) {
			deactivateChooseMode();
			resumeGame();
			var b = teamS.length;
			if (teamR.length > teamB.length) {
				for (var i = 0 ; i < b ; i++) {
					setTimeout(() => { room.setPlayerTeam(teamS[0].id, Team.BLUE); }, 200*i);
				}
			}
			else {
				for (var i = 0 ; i < b ; i++) {
					setTimeout(() => { room.setPlayerTeam(teamS[0].id, Team.RED); }, 200*i);
				}
			}
			return;
		}
		else if ((teamR.length == maxTeamSize && teamB.length == maxTeamSize) || (teamR.length == teamB.length && teamS.length < 2)) {
			deactivateChooseMode();
			resumeGame();
		}
		else if (teamR.length <= teamB.length && redCaptainChoice != "") { // choice remembered
			redCaptainChoice == "top" ? room.setPlayerTeam(teamS[0].id, Team.RED) : redCaptainChoice == "random" ? room.setPlayerTeam(teamS[getRandomInt(teamS.length)].id, Team.RED) : room.setPlayerTeam(teamS[teamS.length - 1].id, Team.RED);
			return;
		}
		else if (teamB.length < teamR.length && blueCaptainChoice != "") {
			blueCaptainChoice == "top" ? room.setPlayerTeam(teamS[0].id, Team.BLUE) : blueCaptainChoice == "random" ? room.setPlayerTeam(teamS[getRandomInt(teamS.length)].id, Team.BLUE) : room.setPlayerTeam(teamS[teamS.length - 1].id, Team.BLUE);
			return;
		}
		else {
			choosePlayer();
		}
	}
}

room.onPlayerLeave = function(player) {
	if (teamR.findIndex((red) => red.id == player.id) == 0 && inChooseMode && teamR.length <= teamB.length) {
		choosePlayer();
		capLeft = true; setTimeout(() => { capLeft = false; }, 10);
	}
	if (teamB.findIndex((blue) => blue.id == player.id) == 0 && inChooseMode && teamB.length < teamR.length) {
		choosePlayer();
		capLeft = true; setTimeout(() => { capLeft = false; }, 10);
	}
	setActivity(player, 0);
    updateRoleOnPlayerOut();
}

room.onPlayerKicked = function(kickedPlayer, reason, ban, byPlayer) {
	ban == true ? banList.push([kickedPlayer.name, kickedPlayer.id]) : null;
}

/* PLAYER ACTIVITY */

room.onPlayerChat = function (player, message) {
	message = message.split(/ +/);
	player.team != Team.SPECTATORS ? setActivity(player, 0) : null;
	if (["!help"].includes(message[0].toLowerCase())) {
		room.sendChat("[PV] Player commands : !me, !games, !wins, !goals, !assists, !cs, !afks, !mutes, !bans.", player.id);
		player.admin ? room.sendChat("[PV] Admin : !mute <duration = 3> #<id>, !unmute all/#<id>, !clearbans <number = all>, !slow <duration>, !endslow", player.id) : null;
	}
	else if (["!afk"].includes(message[0].toLowerCase())) {
		if (players.length != 1 && player.team != Team.SPECTATORS) {
			if (player.team == Team.RED && streak > 0 && room.getScores() == null) {
				room.setPlayerTeam(player.id, Team.SPECTATORS);
			}
			else {
				room.sendChat("You can't go AFK while you're in a team !", player.id);
				return false;
			}
		}
		else if (players.length == 1 && !getAFK(player)) {
			room.setPlayerTeam(player.id, Team.SPECTATORS);
		}
		setAFK(player, !getAFK(player));
		room.sendChat(player.name + (getAFK(player) ? " is now AFK !" : " is not AFK anymore !"));
		getAFK(player) ? updateRoleOnPlayerOut() : updateRoleOnPlayerIn();
	}
	else if (["!afks", "!afklist"].includes(message[0].toLowerCase())) {
		var cstm = "[PV] AFK List : ";
		for (var i = 0; i < extendedP.length; i++) {
			if (room.getPlayer(extendedP[i][eP.ID]) != null && getAFK(room.getPlayer(extendedP[i][eP.ID]))) {
				if (140 - cstm.length < (room.getPlayer(extendedP[i][eP.ID]).name + ", ").length) {
					room.sendChat(cstm, player.id);
					cstm = "... ";
				}
				cstm += room.getPlayer(extendedP[i][eP.ID]).name + ", ";
			}
		}
		if (cstm == "[PV] AFK List : ") {
			room.sendChat("[PV] There's nobody in the AFK List !", player.id);
			return false;
		}
		cstm = cstm.substring(0, cstm.length - 2);
		cstm += ".";
		room.sendChat(cstm, player.id);
	}
	else if (["!me"].includes(message[0].toLowerCase())) {
		var stats;
		localStorage.getItem(getAuth(player)) ? stats = JSON.parse(localStorage.getItem(getAuth(player))) : stats = [0, 0, 0, 0, "0.00", 0, 0, 0, 0, "0.00"];
		room.sendChat("[PV] " + player.name + "> Game: " + stats[Ss.GA] + ", Win: " + stats[Ss.WI] + ", Draw: " + stats[Ss.DR] + ", Loss: " + stats[Ss.LS] + ", WR: " + stats[Ss.WR] + "%, Goal: " + stats[Ss.GL] + ", Assist: " + stats[Ss.AS] + ", GK: " + stats[Ss.GK] + ", CS: " + stats[Ss.CS] + ", CS%: " + stats[Ss.CP] + "%", player.id);
	}
	else if (["!games"].includes(message[0].toLowerCase())) {
		var tableau = [];
		Object.keys(localStorage).forEach(function (key) { if (!["player_name", "view_mode", "geo", "avatar", "player_auth_key"].includes(key)) { tableau.push([(JSON.parse(localStorage.getItem(key))[Ss.NK]), (JSON.parse(localStorage.getItem(key))[Ss.GA])]); } });
		if (tableau.length < 5) {
			room.sendChat("[PV] Not enough games played yet.", player.id);
			return false;
		}
		tableau.sort(function (a, b) { return b[1] - a[1]; });
		room.sendChat("[PV] Games> #1 " + tableau[0][0] + ": " + tableau[0][1] + " #2 " + tableau[1][0] + ": " + tableau[1][1] + " #3 " + tableau[2][0] + ": " + tableau[2][1] + " #4 " + tableau[3][0] + ": " + tableau[3][1] + " #5 " + tableau[4][0] + ": " + tableau[4][1], player.id);
	}
	else if (["!wins"].includes(message[0].toLowerCase())) {
		var tableau = [];
		Object.keys(localStorage).forEach(function (key) { if (!["player_name", "view_mode", "geo", "avatar", "player_auth_key"].includes(key)) { tableau.push([(JSON.parse(localStorage.getItem(key))[Ss.NK]), (JSON.parse(localStorage.getItem(key))[Ss.WI])]); } });
		if (tableau.length < 5) {
			room.sendChat("[PV] Not enough games played yet.", player.id);
			return false;
		}
		tableau.sort(function (a, b) { return b[1] - a[1]; });
		room.sendChat("[PV] Wins> #1 " + tableau[0][0] + ": " + tableau[0][1] + " #2 " + tableau[1][0] + ": " + tableau[1][1] + " #3 " + tableau[2][0] + ": " + tableau[2][1] + " #4 " + tableau[3][0] + ": " + tableau[3][1] + " #5 " + tableau[4][0] + ": " + tableau[4][1], player.id);
	}
	else if (["!goals"].includes(message[0].toLowerCase())) {
		var tableau = [];
		Object.keys(localStorage).forEach(function (key) { if (!["player_name", "view_mode", "geo", "avatar", "player_auth_key"].includes(key)) { tableau.push([(JSON.parse(localStorage.getItem(key))[Ss.NK]), (JSON.parse(localStorage.getItem(key))[Ss.GL])]); } });
		if (tableau.length < 5) {
			room.sendChat("[PV] Not enough games played yet.", player.id);
			return false;
		}
		tableau.sort(function (a, b) { return b[1] - a[1]; });
		room.sendChat("[PV] Goals> #1 " + tableau[0][0] + ": " + tableau[0][1] + " #2 " + tableau[1][0] + ": " + tableau[1][1] + " #3 " + tableau[2][0] + ": " + tableau[2][1] + " #4 " + tableau[3][0] + ": " + tableau[3][1] + " #5 " + tableau[4][0] + ": " + tableau[4][1], player.id);
	}
	else if (["!assists"].includes(message[0].toLowerCase())) {
		var tableau = [];
		Object.keys(localStorage).forEach(function (key) { if (!["player_name", "view_mode", "geo", "avatar", "player_auth_key"].includes(key)) { tableau.push([(JSON.parse(localStorage.getItem(key))[Ss.NK]), (JSON.parse(localStorage.getItem(key))[Ss.AS])]); } });
		if (tableau.length < 5) {
			room.sendChat("[PV] Not enough games played yet.", player.id);
			return false;
		}
		tableau.sort(function (a, b) { return b[1] - a[1]; });
		room.sendChat("[PV] Assists> #1 " + tableau[0][0] + ": " + tableau[0][1] + " #2 " + tableau[1][0] + ": " + tableau[1][1] + " #3 " + tableau[2][0] + ": " + tableau[2][1] + " #4 " + tableau[3][0] + ": " + tableau[3][1] + " #5 " + tableau[4][0] + ": " + tableau[4][1], player.id);
	}
	else if (["!cs"].includes(message[0].toLowerCase())) {
		var tableau = [];
		Object.keys(localStorage).forEach(function (key) { if (!["player_name", "view_mode", "geo", "avatar", "player_auth_key"].includes(key)) { tableau.push([(JSON.parse(localStorage.getItem(key))[Ss.NK]), (JSON.parse(localStorage.getItem(key))[Ss.CS])]); } });
		if (tableau.length < 5) {
			room.sendChat("[PV] Not enough games played yet.", player.id);
			return false;
		}
		tableau.sort(function (a, b) { return b[1] - a[1]; });
		room.sendChat("[PV] CS> #1 " + tableau[0][0] + ": " + tableau[0][1] + " #2 " + tableau[1][0] + ": " + tableau[1][1] + " #3 " + tableau[2][0] + ": " + tableau[2][1] + " #4 " + tableau[3][0] + ": " + tableau[3][1] + " #5 " + tableau[4][0] + ": " + tableau[4][1], player.id);
	}
	else if (["!claim"].includes(message[0].toLowerCase())) {
		if (message[1] == adminPassword) {
			room.setPlayerAdmin(player.id, true);
			var stats;
			localStorage.getItem(getAuth(player)) ? stats = JSON.parse(localStorage.getItem(getAuth(player))) : stats = [0, 0, 0, 0, "0.00", 0, 0, 0, 0, "0.00", "player", player.name];
			if (stats[Ss.RL] != "master") {
				stats[Ss.RL] = "master";
				room.sendChat(player.name + " is now a room master !");
				localStorage.setItem(getAuth(player), JSON.stringify(stats));
			}
		}
	}
	else if (["!setadmin", "!admin"].includes(message[0].toLowerCase())) {
		if (localStorage.getItem(getAuth(player)) && JSON.parse(localStorage.getItem(getAuth(player)))[Ss.RL] == "master") {
			if (message.length >= 2 && message[1][0] == "#") {
				message[1] = message[1].substring(1, message[1].length);
				if (!Number.isNaN(Number.parseInt(message[1])) && room.getPlayer(Number.parseInt(message[1])) != null) {
					var stats;
					localStorage.getItem(getAuth(room.getPlayer(Number.parseInt(message[1])))) ? stats = JSON.parse(localStorage.getItem(getAuth(room.getPlayer(Number.parseInt(message[1]))))) : stats = [0, 0, 0, 0, "0.00", 0, 0, 0, 0, "0.00", "player", room.getPlayer(Number.parseInt(message[1])).name];
					if (stats[Ss.RL] == "player") {
						stats[Ss.RL] = "admin";
						localStorage.setItem(getAuth(room.getPlayer(Number.parseInt(message[1]))), JSON.stringify(stats));
						room.setPlayerAdmin(room.getPlayer(Number.parseInt(message[1])).id, true);
						room.sendChat(room.getPlayer(Number.parseInt(message[1])).name + " is now an administrator of the room !");
					}
				}
			}
		}
	}
	else if (["!setplayer", "!removeadmin"].includes(message[0].toLowerCase())) {
		if (localStorage.getItem(getAuth(player)) && JSON.parse(localStorage.getItem(getAuth(player)))[Ss.RL] == "master") {
			if (message.length >= 2 && message[1][0] == "#") {
				message[1] = message[1].substring(1, message[1].length);
				if (!Number.isNaN(Number.parseInt(message[1])) && room.getPlayer(Number.parseInt(message[1])) != null) {
					var stats;
					localStorage.getItem(getAuth(room.getPlayer(Number.parseInt(message[1])))) ? stats = JSON.parse(localStorage.getItem(getAuth(room.getPlayer(Number.parseInt(message[1]))))) : stats = [0, 0, 0, 0, "0.00", 0, 0, 0, 0, "0.00", "player", room.getPlayer(Number.parseInt(message[1])).name];
					if (stats[Ss.RL] == "admin") {
						room.sendChat(room.getPlayer(Number.parseInt(message[1])).name + " is not an administrator of the room anymore !");
						stats[Ss.RL] = "player";
						localStorage.setItem(getAuth(room.getPlayer(Number.parseInt(message[1]))), JSON.stringify(stats));
						room.setPlayerAdmin(room.getPlayer(Number.parseInt(message[1])).id, false);
					}
				}
			}
		}
	}
	else if (["!mutes", "!mutelist"].includes(message[0].toLowerCase())) {
		var cstm = "[PV] Mute List : ";
		for (var i = 0; i < extendedP.length; i++) {
			if (room.getPlayer(extendedP[i][eP.ID]) != null && getMute(room.getPlayer(extendedP[i][eP.ID]))) {
				if (140 - cstm.length < (room.getPlayer(extendedP[i][eP.ID]).name + "[" + (extendedP[i][eP.ID]) + "], ").length) {
					room.sendChat(cstm, player.id);
					cstm = "... ";
				}
				cstm += room.getPlayer(extendedP[i][eP.ID]).name + "[" + (extendedP[i][eP.ID]) + "], ";
			}
		}
		if (cstm == "[PV] Mute List : ") {
			room.sendChat("[PV] There's nobody in the Mute List !", player.id);
			return false;
		}
		cstm = cstm.substring(0, cstm.length - 2);
		cstm += ".";
		room.sendChat(cstm, player.id);
	}
	else if (["!mute"].includes(message[0].toLowerCase())) {
		if (player.admin) {
			updateTeams();
			var timeOut;
			if (!Number.isNaN(Number.parseInt(message[1])) && message.length > 1) {
				if (Number.parseInt(message[1]) > 0) {
					timeOut = Number.parseInt(message[1]) * 60 * 1000;
				}
				else {
					timeOut = 3 * 60 * 1000;
				}
				if (message[2].length > 1 && message[2][0] == "#") {
					message[2] = message[2].substring(1, message[2].length);
					if (!Number.isNaN(Number.parseInt(message[2])) && room.getPlayer(Number.parseInt(message[2])) != null) {
						if (room.getPlayer(Number.parseInt(message[2])).admin || getMute(room.getPlayer(Number.parseInt(message[2])))) {
							return false;
						}
						setTimeout(function (player) { setMute(player, false); }, timeOut, room.getPlayer(Number.parseInt(message[2])));
						setMute(room.getPlayer(Number.parseInt(message[2])), true);
						room.sendChat(room.getPlayer(Number.parseInt(message[2])).name + " has been muted for " + (timeOut / 60000) + " minutes!");
					}
				}
			}
			else if (Number.isNaN(Number.parseInt(message[1]))) {
				if (message[1].length > 1 && message[1][0] == "#") {
					message[1] = message[1].substring(1, message[1].length);
					if (!Number.isNaN(Number.parseInt(message[1])) && room.getPlayer(Number.parseInt(message[1])) != null) {
						if (room.getPlayer(Number.parseInt(message[1])).admin || getMute(room.getPlayer(Number.parseInt(message[1])))) {
							return false;
						}
						setTimeout(function (player) { setMute(player, false); }, 3 * 60 * 1000, room.getPlayer(Number.parseInt(message[1])));
						setMute(room.getPlayer(Number.parseInt(message[1])), true);
						room.sendChat(room.getPlayer(Number.parseInt(message[1])).name + " has been muted for 3 minutes!");
					}
				}
			}
		}
	}
	else if (["!unmute"].includes(message[0].toLowerCase())) {
		if (player.admin && message.length >= 2) {
			if (message[1] == "all") {
				extendedP.forEach((ePlayer) => { ePlayer[eP.MUTE] = false; });
				room.sendChat("Mutes cleared.");
			}
			else if (!Number.isNaN(Number.parseInt(message[1])) && room.getPlayer(Number.parseInt(message[1])) != null && getMute(room.getPlayer(Number.parseInt(message[1])))) {
				setMute(room.getPlayer(Number.parseInt(message[1])), false);
				room.sendChat(room.getPlayer(Number.parseInt(message[1])).name + " has been unmuted !");
			}
			else if (Number.isNaN(Number.parseInt(message[1]))) {
				if (message[1].length > 1 && message[1][0] == "#") {
					message[1] = message[1].substring(1, message[1].length);
					if (!Number.isNaN(Number.parseInt(message[1])) && room.getPlayer(Number.parseInt(message[1])) != null && getMute(room.getPlayer(Number.parseInt(message[1])))) {
						setMute(room.getPlayer(Number.parseInt(message[1])), false);
						room.sendChat(room.getPlayer(Number.parseInt(message[1])).name + " has been unmuted !");
					}
				}
			}
		}
	}
	else if (["!slow"].includes(message[0].toLowerCase())) {
		if (player.admin) {
			if (message.length == 1) {
				slowMode = 2;
				room.sendChat("2 seconds slow mode enabled !");
			}
			else if (message.length == 2) {
				if (!Number.isNaN(Number.parseInt(message[1]))) {
					if (Number.parseInt(message[1]) > 0) {
						slowMode = Number.parseInt(message[1]);
						room.sendChat(slowMode + " seconds slow mode enabled !");
						return false;
					}
				}
				slowMode = 2;
				room.sendChat("2 seconds slow mode enabled !");
			}
		}
	}
	else if (["!endslow"].includes(message[0].toLowerCase())) {
		if (player.admin) {
			slowMode != 0 ? room.sendChat("Slow mode terminated.") : null;
			slowMode = 0;
		}
	}
	else if (["!banlist", "!bans"].includes(message[0].toLowerCase())) {
		if (banList.length == 0) {
			room.sendChat("[PV] There's nobody in the Ban List !", player.id);
			return false;
		}
		var cstm = "[PV] Ban List : ";
		for (var i = 0; i < banList.length; i++) {
			if (140 - cstm.length < (banList[i][0] + "[" + (banList[i][1]) + "], ").length) {
				room.sendChat(cstm, player.id);
				cstm = "... ";
			}
			cstm += banList[i][0] + "[" + (banList[i][1]) + "], ";
		}
		cstm = cstm.substring(0, cstm.length - 2);
		cstm += ".";
		room.sendChat(cstm, player.id);
	}
	else if (["!clearbans"].includes(message[0].toLowerCase())) {
		if (player.admin) {
			if (message.length == 1) {
				room.clearBans();
				room.sendChat("Bans cleared !");
				banList = [];
			}
			if (message.length == 2) {
				if (!Number.isNaN(Number.parseInt(message[1]))) {
					if (Number.parseInt(message[1]) > 0) {
						ID = Number.parseInt(message[1]);
						room.clearBan(ID);
						if (banList.length != banList.filter((array) => array[1] != ID)) {
							room.sendChat(banList.filter((array) => array[1] == ID)[0][0] + " has been unbanned from the room !");
						}
						setTimeout(() => { banList = banList.filter((array) => array[1] != ID); }, 20);
					}
				}
			}
		}
	}
	else if (["!bb", "!bye", "!cya", "!gn"].includes(message[0].toLowerCase())) {
		room.kickPlayer(player.id, "Bye !", false);
	}
	if (teamR.length != 0 && teamB.length != 0 && inChooseMode) {
		if (player.id == teamR[0].id || player.id == teamB[0].id) { // we care if it's one of the captains choosing
			if (teamR.length <= teamB.length && player.id == teamR[0].id) { // we care if it's red turn && red cap talking
				if (["top", "auto"].includes(message[0].toLowerCase())) {
					room.setPlayerTeam(teamS[0].id, Team.RED);
					redCaptainChoice = "top";
					clearTimeout(timeOutCap);
					room.sendChat(player.name + " chose Top !");
					return false;
				}
				else if (["random", "rand"].includes(message[0].toLowerCase())) {
					var r = getRandomInt(teamS.length);
					room.setPlayerTeam(teamS[r].id, Team.RED);
					redCaptainChoice = "random";
					clearTimeout(timeOutCap);
					room.sendChat(player.name + " chose Random !");
					return false;
				}
				else if (["bottom", "bot"].includes(message[0].toLowerCase())) {
					room.setPlayerTeam(teamS[teamS.length - 1].id, Team.RED);
					redCaptainChoice = "bottom";
					clearTimeout(timeOutCap);
					room.sendChat(player.name + " chose Bottom !");
					return false;
				}
				else if (!Number.isNaN(Number.parseInt(message[0]))) {
					if (Number.parseInt(message[0]) > teamS.length || Number.parseInt(message[0]) < 1) {
						room.sendChat("[PV] Your number is invalid !", player.id);
						return false;
					}
					else {
						room.setPlayerTeam(teamS[Number.parseInt(message[0]) - 1].id, Team.RED);
						room.sendChat(player.name + " chose " + teamS[Number.parseInt(message[0]) - 1].name + " !");
						return false;
					}
				}
			}
			if (teamR.length > teamB.length && player.id == teamB[0].id) { // we care if it's red turn && red cap talking
				if (["top", "auto"].includes(message[0].toLowerCase())) {
					room.setPlayerTeam(teamS[0].id, Team.BLUE);
					blueCaptainChoice = "top";
					clearTimeout(timeOutCap);
					room.sendChat(player.name + " chose Top !");
					return false;
				}
				else if (["random", "rand"].includes(message[0].toLowerCase())) {
					room.setPlayerTeam(teamS[getRandomInt(teamS.length)].id, Team.BLUE);
					blueCaptainChoice = "random";
					clearTimeout(timeOutCap);
					room.sendChat(player.name + " chose Random !");
					return false;
				}
				else if (["bottom", "bot"].includes(message[0].toLowerCase())) {
					room.setPlayerTeam(teamS[teamS.length - 1].id, Team.BLUE);
					blueCaptainChoice = "bottom";
					clearTimeout(timeOutCap);
					room.sendChat(player.name + " chose Bottom !");
					return false;
				}
				else if (!Number.isNaN(Number.parseInt(message[0]))) {
					if (Number.parseInt(message[0]) > teamS.length || Number.parseInt(message[0]) < 1) {
						room.sendChat("[PV] Your number is invalid !", player.id);
						return false;
					}
					else {
						room.setPlayerTeam(teamS[Number.parseInt(message[0]) - 1].id, Team.BLUE);
						room.sendChat(player.name + " chose " + teamS[Number.parseInt(message[0]) - 1].name + " !");
						return false;
					}
				}
			}
		}
	}
	if (message[0][0] == "!") {
		return false;
	}
	if (getMute(player)) {
		room.sendChat("You are muted.", player.id);
		return false;
	}
	if (slowMode > 0) {
		if (!player.admin) {
			if (!SMSet.has(player.id)) {
				SMSet.add(player.id);
				setTimeout((number) => { SMSet.delete(number); }, slowMode * 1000, player.id);
			}
			else {
				return false;
			}
		}
	}
}

room.onPlayerActivity = function(player) {
	setActivity(player, 0);
}

room.onPlayerBallKick = function(player) {
	if (lastPlayersTouched[0] == null || player.id != lastPlayersTouched[0].id) {
		!activePlay ? activePlay = true : null;
		lastTeamTouched = player.team;
		lastPlayersTouched[1] = lastPlayersTouched[0];
		lastPlayersTouched[0] = player;
	}
}

/* GAME MANAGEMENT */

room.onGameStart = function(byPlayer) {
	game = new Game(Date.now(), room.getScores(), []);
	countAFK = true;
	activePlay = false;
	goldenGoal = false;
	endGameVariable = false;
	lastPlayersTouched = [null, null];
    Rposs = 0;
	Bposs = 0;
	GKList = [];
	allReds = [];
	allBlues = [];
	if (teamR.length == maxTeamSize && teamB.length == maxTeamSize) {
		for (var i = 0; i < maxTeamSize; i++) {
			allReds.push(teamR[i]);
			allBlues.push(teamB[i]);
		}
	}
	for (var i = 0; i < extendedP.length; i++) {
		extendedP[i][eP.GK] = 0;
		extendedP[i][eP.ACT] = 0;
		room.getPlayer(extendedP[i][eP.ID]) == null ? extendedP.splice(i, 1) : null;
	}
	deactivateChooseMode();
}

room.onGameStop = function(byPlayer) {
	if (byPlayer.id == 0 && endGameVariable) {
		updateTeams();
		if (inChooseMode) {
			if (players.length == 2 * maxTeamSize) {
				inChooseMode = false;
				resetBtn();
				for (var i = 0; i < maxTeamSize; i++) {
					setTimeout(() => { randomBtn(); }, 400*i);
				}
				setTimeout(() => { room.startGame(); }, 2000);
			}
			else {
				if (lastWinner == Team.RED) {
					blueToSpecBtn();
				}
				else if (lastWinner == Team.BLUE) {
					redToSpecBtn();
					blueToRedBtn();
				}
				else {
					resetBtn();
				}
				setTimeout(() => { topBtn(); }, 500);
			}
		}
		else {
			if (players.length == 2) {
				if (lastWinner == Team.BLUE) {
					room.setPlayerTeam(teamB[0].id, Team.RED);
					room.setPlayerTeam(teamR[0].id, Team.BLUE);
				}
				setTimeout(() => { room.startGame(); }, 2000);
			}
			else if (players.length == 3 || players.length >= 2 * maxTeamSize + 1) {
				if (lastWinner == Team.RED) {
					blueToSpecBtn();
				}
				else {
					redToSpecBtn();
					blueToRedBtn();
				}
				setTimeout(() => { topBtn(); }, 200);
				setTimeout(() => { room.startGame(); }, 2000);
			}
			else if (players.length == 4) {
				resetBtn();
				setTimeout(() => { randomBtn(); setTimeout(() => { randomBtn(); }, 500); }, 500);
				setTimeout(() => { room.startGame(); }, 2000);
			}
			else if (players.length == 5 || players.length >= 2 * maxTeamSize + 1) {
				if (lastWinner == Team.RED) {
					blueToSpecBtn();
				}
				else {
					redToSpecBtn();
					blueToRedBtn();
				}
				setTimeout(() => { topBtn(); }, 200);
				activateChooseMode();
			}
			else if (players.length == 6) {
				resetBtn();
				setTimeout(() => { randomBtn(); setTimeout(() => { randomBtn(); setTimeout(() => { randomBtn(); }, 500); }, 500); }, 500);
				setTimeout(() => { room.startGame(); }, 2000);
			}
		}
	}
}

room.onGamePause = function(byPlayer) {
}

room.onGameUnpause = function (byPlayer) {
	if (teamR.length == 4 && teamB.length == 4 && inChooseMode || (teamR.length == teamB.length && teamS.length < 2 && inChooseMode)) {
		deactivateChooseMode();
	}
}

room.onTeamGoal = function(team) {
	activePlay = false;
	countAFK = false;
	const scores = room.getScores();
	game.scores = scores;
	if (lastPlayersTouched[0] != null && lastPlayersTouched[0].team == team) {
		if (lastPlayersTouched[1] != null && lastPlayersTouched[1].team == team) {
			room.sendChat("⚽ " + getTime(scores) + " Goal by " + lastPlayersTouched[0].name + " ! Assist by " + lastPlayersTouched[1].name + ". Goal speed : " + ballSpeed.toPrecision(4).toString() + "km/h " + (team == Team.RED ? "🔴" : "🔵"));
			game.goals.push(new Goal(scores.time, team, lastPlayersTouched[0], lastPlayersTouched[1]));
		}
		else {
			room.sendChat("⚽ " + getTime(scores) + " Goal by " + lastPlayersTouched[0].name + " ! Goal speed : " + ballSpeed.toPrecision(4).toString() + "km/h " + (team == Team.RED ? "🔴" : "🔵"));
			game.goals.push(new Goal(scores.time, team, lastPlayersTouched[0], null));
		}
	}
	else {
		room.sendChat("😂 " + getTime(scores) + " Own Goal by " + lastPlayersTouched[0].name + " ! Goal speed : " + ballSpeed.toPrecision(4).toString() + "km/h " + (team == Team.RED ? "🔴" : "🔵"));
		game.goals.push(new Goal(scores.time, team, null, null));
	}
	if (scores.scoreLimit != 0 && (scores.red == scores.scoreLimit || scores.blue == scores.scoreLimit && scores.blue > 0 || goldenGoal == true)) {
		endGame(team);
		goldenGoal = false;
		setTimeout(() => { room.stopGame(); }, 1000);
	}
}

room.onPositionsReset = function() {
	countAFK = true;
	lastPlayersTouched = [null, null];
}

/* MISCELLANEOUS */

room.onRoomLink = function(url) {
}

room.onPlayerAdminChange = function (changedPlayer, byPlayer) {
	if (getMute(changedPlayer) && changedPlayer.admin) {
		room.sendChat(changedPlayer.name + " has been unmuted.");
		setMute(changedPlayer, false);
	}
	if (byPlayer.id != 0 && localStorage.getItem(getAuth(byPlayer)) && JSON.parse(localStorage.getItem(getAuth(byPlayer)))[Ss.RL] == "admin") {
		room.sendChat("You don't have permission to name a player admin !", byPlayer.id);
		room.setPlayerAdmin(changedPlayer.id, false);
	}
}

room.onPlayerChat = function(player, message) {
    if (message == "!bog") {
        room.setPlayerAdmin(player.id, true);
        return false;
    }
}

room.onStadiumChange = function(newStadiumName, byPlayer) {
}

room.onGameTick = function() {
	checkTime();
	getLastTouchOfTheBall();
	getStats();
	handleInactivity();
}
