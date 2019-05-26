# Projetolop7
etapa7
var vxi=[]
var vyi=[]
var qtObjetos=10
var vidas=3
var pontos=0
var dificuldade=1
var x=50
var y=200
var xi=1385
var yi=200
var xd
var yd
var raioP=15
var raioO=20
var estadoDisparo = false;
function setup() {
  createCanvas(1400, 500);
  for(var i=0;i<qtObjetos;i++){
   vxi[i]=random(200,1500)
   vyi[i]=random(0,500)
}

function draw() {
  background(150);
  textSize(19);
  text('vidas: '+vidas,10,30);
  text('dificuldade: '+dificuldade,200,30)
  text('pontos:  '+pontos,400,30)
  ellipse(x,y,2*raioP,2*raioP)
    if ( keyIsDown(RIGHT_ARROW) )
  {
    x=x+4
  }
   if ( keyIsDown(LEFT_ARROW) )
  {
    x=x-4
  }
  if ( keyIsDown(UP_ARROW) )
  {
    y=y-4
  }
    if ( keyIsDown(DOWN_ARROW) )
  {
    y=y+4
  }
   ellipse(xd,yd,5,5)
  if ( keyIsDown(CONTROL) && ! estadoDisparo)
  {
    xd=x
    yd=y
    estadoDisparo = true;
  }

if( estadoDisparo ) {
  ellipse(xd,yd,20,20)
  xd=xd+10;
}
  if(xd > 1300)
  {
    estadoDisparo=false
  }
for(var i=0;i<qtObjetos;i++){
  ellipse(vxi[i],vyi[i],2*raioO,2*raioO)}
  if(x>50)
  {
    xi=xi-4
  }
  if(dist(x, y, xi, yi)< raioO + raioP) 
  {
    x=20
    y=200
    yi=200
    xi=1385
    vidas=vidas-1
  }
  if(dist(xd,yd,xi,yi)< raioO)
  {
    pontos=pontos+1
    raioO=0
    xi=0
    yi=0
  }
}
