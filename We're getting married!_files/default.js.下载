$(document).ready(function() {
  
  /*
   * jQuery Timer Plugin
   * http://www.evanbot.com/article/jquery-timer-plugin/23
   *
   * @version      1.0
   * @copyright    2009 Evan Byrne (http://www.evanbot.com)
   */ 

  jQuery.timer = function(time,func,callback){
  	var a = {timer:setTimeout(func,time),callback:null}
  	if(typeof(callback) == 'function'){a.callback = callback;}
  	return a;
  };

  jQuery.clearTimer = function(a){
  	clearTimeout(a.timer);
  	if(typeof(a.callback) == 'function'){a.callback();};
  	return this;
  };
  
/*
  //Lazy Load images
  $("img").lazyload({
    threshold : 200,
    container: $(".slideshow")
  });
*/

// RSVP Form Submit
$('#rsvp .submit').click(function(){
  $('#rsvp .submit').hide();
});
$(function(){
  $("#rsvp-form").submit(function(){
      dataString = $("#rsvp-form").serialize();
      $('#rsvp-form .error').remove()
      //var form_html = $("#rsvp-form");
      //console.debug(form_html);
      //$('#rsvp-form').fadeOut();
      
      $.ajax({
        type: "POST",
        url: "rsvp-process.php",
        data: dataString,
        dataType: "json",
        success: function(data) {
          if ( data.status == 'pass' ) {
            $('#rsvp-form').fadeOut(function(){
              
              $('#rsvp-form').html('<div class="rsvp-received">' +data.response+ '</div>').fadeIn(1000);
              
            });
            
            myTimer = $.timer(2500,function(){
            
              $('#rsvp .rsvp-link').click();
            
            });
                      
          }
          else {
          
            $('#rsvp-form').append('<div class="error">' +data.response+ '</div>');
            $('#rsvp .submit').fadeIn('500');
            console.debug(data);

          }
        }
      });

      return false;            

  });
});

  $(function() {
      $('ul.nav a').bind('click',function(event){
          var $anchor = $(this);
        
          $('html, body').stop().animate({
              scrollTop: $($anchor.attr('href')).offset().top
          }, 1500,'easeInOutExpo');
          /*
          if you don't want to use the easing effects:
          $('html, body').stop().animate({
              scrollTop: $($anchor.attr('href')).offset().top
          }, 1000);
          */
          event.preventDefault();
      });
  });

  $('#nav-rsvp a').unbind();
  $('#nav-rsvp a, .rsvp-link').click(function(){
    if ( $('#header').hasClass('open') ) {
      $('#header').animate({
      top: '-=115'
      }, 750, 'easeInOutCubic');
      $('#header').removeClass('open');
    } 
    else {
      $('#header').animate({
      top: '+=115'
      }, 750, 'easeInOutCubic');
      $('#header').addClass('open'); 
    }
    return false;
  });
  
  
  
  // Photos Slideshot
  $('#section-3 .slideshow').jcarousel({
    scroll: 1,
    animation: 500,
    easing: 'easeInOutSine',
    wrap: 'last',
    initCallback: photos_initCallback,
    itemVisibleInCallback: photos_activeSlide,
  });
    
  function photos_initCallback(carousel) {
    $('#section-3 .slideshow-control li').bind('click', function() {
      $('#section-3 .slideshow-control li').removeClass('active');  
      $(this).addClass('active');  
      carousel.scroll($.jcarousel.intval($(this).text()));
      
      return false;
    });
  };

  function photos_activeSlide(carousel, object, intval, state) {
    intval--;
    $('#section-3 .slideshow-control li').removeClass('active');
    $('#section-3 .slideshow-control li:eq('+intval+')').addClass('active');
    
  }

  $('#section-3 .slideshow-control').width( ($('#section-3 .slideshow-control li').length * 30) + 'px');

  
  // Groomsmen Slideshow
  $('#section-4 .slideshow').jcarousel({
    scroll: 1,
    animation: 500,
    easing: 'easeInOutSine',
    wrap: 'last',
    initCallback: grooms_initCallback,
    itemVisibleInCallback: grooms_activeSlide,
  });
    
  function grooms_initCallback(carousel) {
    $('#section-4 .slideshow-control li').bind('click', function() {
      $('#section-4 .slideshow-control li').removeClass('active');  
      $(this).addClass('active');  
      carousel.scroll($.jcarousel.intval($(this).text()));
      
      return false;
    });
  };

  function grooms_activeSlide(carousel, object, intval, state) {
    intval--;
    $('#section-4 .slideshow-control li').removeClass('active');
    $('#section-4 .slideshow-control li:eq('+intval+')').addClass('active');
    
  }
  
  $('#section-4 .slideshow-control').width( ($('#section-4 .slideshow-control li').length * 30) + 'px');
  

  // Bridesmaids Slideshow
  $('#section-5 .slideshow').jcarousel({
    scroll: 1,
    animation: 500,
    easing: 'easeInOutSine',
    wrap: 'last',
    initCallback: brides_initCallback,
    itemVisibleInCallback: brides_activeSlide,
  });
    
  function brides_initCallback(carousel) {
    $('#section-5 .slideshow-control li').bind('click', function() {
      $('#section-5 .slideshow-control li').removeClass('active');  
      $(this).addClass('active');  
      carousel.scroll($.jcarousel.intval($(this).text()));
      
      return false;
    });
  };

  function brides_activeSlide(carousel, object, intval, state) {
    intval--;
    $('#section-5 .slideshow-control li').removeClass('active');
    $('#section-5 .slideshow-control li:eq('+intval+')').addClass('active');
    
  }

  $('#section-5 .slideshow-control').width( ($('#section-5 .slideshow-control li').length * 30) + 'px');

  

});