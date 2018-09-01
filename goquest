// ==UserScript==
// @name         GoQuest
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  try to take over the world!
// @author       You
// @match        http://wars.fm/*
// @grant        none
// @require      http://code.jquery.com/jquery-1.12.4.min.js
// ==/UserScript==

(function() {
    'use strict';
    var click_times = 0;
    var pass_times = 0;
    function run(){
        console.log('setInterval');
        if($('#game').attr('style')=="display: block;"){
            if($('#game > div.result.movable-alert-box').attr('style')=="display: block;"){
                console.log('play-again');
                click_times = 0;
                pass_times = 0;
                $('#play-again-button').click();
            } else {
                if($('.player0.turn-to-play').length>=1){
                    var mat = $('#lastmove').text().match(/(\d+)\..+/);
                    if(!mat || $('#lastmove').text().match(/(\d+)\..+/)[1]<30){
                        click_times += 1;
                        console.log('click: '+click_times);
                        var len = $('.position .board .square .piece:not(.sb):not(.sb)').length;
                        $('.position .board .square .piece:not(.sb):not(.sb)').eq(Math.floor(Math.random()*len)).click();
                    } else {
                        if(pass_times<=10){
                            console.log('pass-button');
                            $('#pass-button').click();
                            pass_times += 1;
                        } else {
                            console.log('No Pass');
                        }
                       //console.log('resign');
                       //$('#resign-button').click();
                    }
                } else {
                    console.log('wait for click');
                }
            }
        }
        if($('#home').attr('style')!="display: none;"){
            console.log('play-online');
            click_times = 0;
            pass_times = 0;
            $('#play-button').click();
        }
        window.mytimer = setTimeout(function(){run();}, Math.random()*5000+2000);
    }
    // clearInterval(window.mytimer)
    // window.mytimer = setInterval(function(){
    window.mytimer = setTimeout(function(){run();}, Math.random()*5000+2000);
})();
