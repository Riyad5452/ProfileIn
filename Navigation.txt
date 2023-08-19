/* Jquery el */

var words = ['View Data Dashboard Below','Mediceram','Your Trusted Ceramic Formers Supplier', 'Visit also Robert Lancaon Hortal Youtube Videos'],
    part,
    i = 0,
    offset = 0,
    len = words.length,
    forwards = true,
    skip_count = 0,
    skip_delay = 15,
    speed = 70;



var wordflick = function () {
  setInterval(function () {
    if (forwards) {
      if (offset >= words[i].length) {
        ++skip_count;
        if (skip_count == skip_delay) {
          forwards = false;
          skip_count = 0;
        }
      }
    }
    else {
      if (offset == 0) {
        forwards = true;
        i++;
        offset = 0;
        if (i >= len) {
          i = 0;
        }
      }
    }
    part = words[i].substr(0, offset);
    if (skip_count == 0) {
      if (forwards) {
        offset++;
      }
      else {
        offset--;
      }
    }
    $('#info').text(part);
  },speed);
};






$(document).ready(function(){
  wordflick();
    $("#menu-toggle").click(function(e){
      e.preventDefault();
     
      $("#wrapper").toggleClass("menuDisplayed"); 
      $(".navbar-brand").show();
    });

  });






  tday  =new Array("Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday");
  tmonth=new Array("January","February","March","April","May","June","July","August","September","October","November","December");

  function GetClock(){
  tzOffset = +8; //set this to the number of hours offset from UTC

  d = new Date();
  dx = d.toGMTString();
  dx = dx.substr(0,dx.length -3);
  d.setTime(Date.parse(dx))
  d.setHours(d.getHours() + tzOffset);
  nday   = d.getDay();
  nmonth = d.getMonth();
  ndate  = d.getDate();
  nyear = d.getYear();
  nhour  = d.getHours();
  nmin   = d.getMinutes();
  nsec   = d.getSeconds();

  if(nyear<1000) nyear=nyear+1900;

       if(nhour ==  0) {ap = " AM";nhour = 12;}
  else if(nhour <= 11) {ap = " AM";}
  else if(nhour == 12) {ap = " PM";}
  else if(nhour >= 13) {ap = " PM";nhour -= 12;}

  if(nmin <= 9) {nmin = "0" +nmin;}
  if(nsec <= 9) {nsec = "0" +nsec;}


  document.getElementById('clockbox').innerHTML=""+tday[nday]+", "+tmonth[nmonth]+" "+ndate+", "+nyear+" "+nhour+":"+nmin+":"+nsec+ap+"";
  setTimeout("GetClock()", 1000);
  }
  window.onload=GetClock;








  /*mga mawawala pag click kulektahin  glyphicon glyphicon-remove add class  pemedes approach  my nav on my peronal work email na di ko naman ginamit  */ 