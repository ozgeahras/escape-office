<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Escape Office</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
    <script src="https://ajax.googleapis.com/ajax/libs/jqueryui/1.11.4/jquery-ui.min.js" type="text/javascript"></script>

    <!-- <link rel="stylesheet" href="style.css"> -->
    <style>
        @import url('https://fonts.googleapis.com/css?family=Merriweather|Pacifico|Permanent+Marker');
        body {
            cursor: default;
            background-color: #A5D8DB;
            font-family: 'Merriweather', serif;
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
            overflow: hidden;
            -webkit-text-size-adjust: none;
            -moz-text-size-adjust: none;
            -ms-text-size-adjust: none;
            text-size-adjust: none;
        }
        
        p.mobile {
            color: #F46E65;
            font-size: 1em;
            text-align: center;
            margin-top: 80px;
            line-height: 40px;
            display: none;
        }
        
        #scene {
            width: 1000px;
            height: 700px;
            padding: 10px;
            margin: 0 auto;
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            display: block;
        }
        
        h1 {
            color: #6686BF;
            text-align: center;
            font-size: 100px;
            line-height: 80px;
        }
        
        h2 {
            color: #6686BF;
            text-align: center;
            font-size: 30px;
            line-height: 5px;
        }
        /*CLOCK*/
        
        #clock {
            height: 100px;
            width: 100px;
            border-radius: 50%;
            border: 10px solid #3E3F4B;
            background-color: #FFF;
            position: absolute;
            cursor: pointer;
            margin-left: 400px;
            -webkit-box-shadow: inset 10px 10px 8px #A5D8DB;
            box-shadow: inset 10px 10px 8px #A5D8DB;
        }
        
        #clock-face {
            height: 90px;
            width: 90px;
            border-radius: 50%;
            background-color: #FFF;
            margin: auto;
            position: relative;
            top: 50%;
            -webkit-transform: translateY(-50%);
            -ms-transform: translateY(-50%);
            transform: translateY(-50%);
        }
        
        .clock-marker {
            background-color: #A5D8DB;
            height: 100%;
            width: 2px;
            position: absolute;
            z-index: 0;
            left: 50%;
            margin-left: -1px;
            top: 0
        }
        
        #clock-marker-12-6 {
            background-color: #5FBABF;
        }
        
        #clock-marker-1-7 {
            -webkit-transform: rotate(30deg);
            -ms-transform: rotate(30deg);
            transform: rotate(30deg);
        }
        
        #clock-marker-2-8 {
            -webkit-transform: rotate(60deg);
            -ms-transform: rotate(60deg);
            transform: rotate(60deg);
        }
        
        #clock-marker-3-9 {
            -webkit-transform: rotate(90deg);
            -ms-transform: rotate(90deg);
            transform: rotate(90deg);
            background-color: #5FBABF;
        }
        
        #clock-marker-4-10 {
            -webkit-transform: rotate(120deg);
            -ms-transform: rotate(120deg);
            transform: rotate(120deg);
        }
        
        #clock-marker-5-11 {
            -webkit-transform: rotate(150deg);
            -ms-transform: rotate(150deg);
            transform: rotate(150deg);
        }
        
        #clock-inner {
            height: 70px;
            width: 70px;
            border-radius: 50%;
            background-color: #FFF;
            margin: auto;
            position: relative;
            top: 50%;
            -webkit-transform: translateY(-50%);
            -ms-transform: translateY(-50%);
            transform: translateY(-50%);
        }
        
        #clock-dot {
            width: 5px;
            height: 5px;
            border-radius: 50%;
            background-color: #3E3F4B;
            position: absolute;
            top: 50%;
            left: 50%;
            margin-left: -2.5px;
            margin-top: -2.5px;
        }
        
        .hand,
        .hand.hour {
            position: absolute;
            width: 4px;
            height: 30%;
            top: 20%;
            left: 50%;
            margin-left: -2px;
            background-color: #F47164;
            -webkit-transform: rotate(35deg);
            -ms-transform: rotate(35deg);
            transform: rotate(35deg);
            -webkit-transform-origin: bottom;
            -ms-transform-origin: bottom;
            transform-origin: bottom;
            -webkit-animation: spin 43200s infinite linear;
            animation: spin 43200s infinite linear;
        }
        
        .hand.minute {
            height: 45%;
            top: 5%;
            width: 3px;
            margin-left: -1.5px;
            -webkit-transform: rotate(50deg);
            -ms-transform: rotate(50deg);
            transform: rotate(50deg);
            -webkit-transform-origin: bottom;
            -ms-transform-origin: bottom;
            transform-origin: bottom;
            -webkit-animation: spin 3600s infinite linear;
            animation: spin 3600s infinite linear;
        }
        
        .hand.second {
            height: 50%;
            width: 2px;
            margin-left: -1px;
            top: 0;
            background-color: #3E3F4B;
            -webkit-transform: rotate(0deg);
            -ms-transform: rotate(0deg);
            transform: rotate(0deg);
            -webkit-transform-origin: bottom;
            -ms-transform-origin: bottom;
            transform-origin: bottom;
            -webkit-animation: spin 60s infinite steps(60);
            animation: spin 60s infinite steps(60);
        }
        
        @-webkit-keyframes spin {
            100% {
                -webkit-transform: rotate(360deg);
                transform: rotate(360deg);
            }
        }
        
        @keyframes spin {
            100% {
                -webkit-transform: rotate(360deg);
                transform: rotate(360deg);
            }
        }
        
        @-webkit-keyframes spin-minute {
            100% {
                -webkit-transform: rotate(410deg);
                transform: rotate(410deg);
            }
        }
        
        @keyframes spin-minute {
            100% {
                -webkit-transform: rotate(410deg);
                transform: rotate(410deg);
            }
        }
        
        @-webkit-keyframes spin-hour {
            100% {
                -webkit-transform: rotate(395deg);
                transform: rotate(395deg);
            }
        }
        
        @keyframes spin-hour {
            100% {
                -webkit-transform: rotate(395deg);
                transform: rotate(395deg);
            }
        }
        
        #clock:hover .hand.minute {
            -webkit-animation: spin-minute 2s infinite linear;
            animation: spin-minute 2s infinite linear;
        }
        
        #clock:hover .hand.hour {
            -webkit-animation: spin-hour 4s infinite linear;
            animation: spin-hour 4s infinite linear;
        }
        
        #clock:hover .hand.second {
            -webkit-animation: spin 1s infinite linear;
            animation: spin 1s infinite linear;
        }
        /*END OF CLOCK*/
        /*DESK*/
        
        #desk {
            bottom: 0;
            width: 800px;
            height: 280px;
            margin-left: 100px;
            position: absolute;
        }
        
        #desk-top-1,
        #desk-top-2,
        #desk-top-3 {
            background-color: #F47164;
            position: absolute;
            z-index: 100;
        }
        
        #desk-top-1 {
            width: 100%;
            height: 8px;
        }
        
        #desk-top-2 {
            width: 98%;
            height: 15px;
            margin-left: 8px;
            margin-top: 8px;
        }
        
        #desk-top-3 {
            width: 95%;
            height: 20px;
            margin-left: 18px;
            margin-top: 23px;
        }
        
        #desk-top-3-left,
        #desk-top-3-right {
            background-color: #A5D8DB;
            width: 20px;
            height: 100%;
            z-index: 1;
            position: absolute;
            border-radius: 50%;
            margin-top: 8px;
        }
        
        #desk-top-3-left {
            margin-left: -8px;
            left: 0;
        }
        
        #desk-top-3-right {
            margin-right: -8px;
            right: 0;
        }
        
        #desk-leg-left,
        #desk-leg-right {
            z-index: 5;
            position: absolute;
            border-left: solid 25px #F47164;
            height: 240px;
            margin-top: 43px;
        }
        
        #desk-leg-left {
            margin-left: 40px;
        }
        
        #desk-leg-right {
            margin-left: 730px;
        }
        /*END OF DESK*/
        /*BOOK STACK*/
        
        #stack-book {
            width: 135px;
            height: auto;
            display: inline-block;
            margin-top: 270px;
            margin-left: 150px;
            cursor: pointer;
            position: absolute;
            z-index: 100;
        }
        
        #stack-book-1,
        .stack-book-2,
        .stack-book-3,
        .stack-book-4,
        #stack-book-5,
        .stack-book-6,
        .stack-book-7,
        #stack-book-8,
        .stack-book-9,
        #stack-book-10,
        #stack-book-11,
        #stack-book-12 {
            position: relative;
            -webkit-box-shadow: inset 1px 1px 1px rgba(0, 0, 0, 0.2);
            box-shadow: inset 1px 1px 1px rgba(0, 0, 0, 0.2);
            top: 0;
        }
        
        #stack-book-1 {
            background-color: #FFF;
            height: 3px;
            width: 100px;
            border: solid 3px #84A840;
            border-left: none;
        }
        
        .stack-book-2 {
            background-color: #FFF;
            height: 5px;
            width: 100px;
            border: solid 3px #6787C0;
            border-left: none;
            margin-left: 5px;
            -webkit-transform: skew(15deg);
            -ms-transform: skew(15deg);
            transform: skew(15deg);
        }
        
        .stack-book-3 {
            background-color: #FFF;
            height: 8px;
            width: 105px;
            border: solid 4px #6787C0;
            border-right: none;
            margin-left: 8px;
            -webkit-transform: skew(-10deg);
            -ms-transform: skew(-10deg);
            transform: skew(-10deg);
        }
        
        .stack-book-4 {
            background-color: #FFF;
            height: 15px;
            width: 110px;
            border: solid 4px #81A748;
            border-right: none;
            border-left: none;
            margin-left: 0px;
        }
        
        #stack-book-5 {
            background-color: #FCD57E;
            height: 8px;
            width: 110px;
            border: solid 6px #EABBAE;
            border-right: none;
            margin-left: 10px;
            -webkit-transform: skew(10deg);
            -ms-transform: skew(10deg);
            transform: skew(10deg);
        }
        
        .stack-book-6 {
            background-color: #FCD57E;
            height: 0px;
            width: 110px;
            border: solid 3px #698CC1;
            border-right: none;
            margin-left: 0px;
        }
        
        .stack-book-7 {
            background-color: #FFF;
            height: 15px;
            width: 115px;
            border: solid 6px #F47164;
            border-left: none;
            border-right: none;
            margin-left: 4px;
            -webkit-transform: skew(-10deg);
            -ms-transform: skew(-10deg);
            transform: skew(-10deg);
        }
        
        #stack-book-8 {
            background-color: #FFF;
            height: 0px;
            width: 115px;
            border: solid 3px #81A748;
            border-left: none;
            border-right: none;
            margin-left: 15px;
        }
        
        #stack-book-9 {
            background-color: #FCD57E;
            height: 6px;
            width: 115px;
            border: solid 4px #EABBAE;
            border-left: none;
            border-right: none;
            margin-left: 0px;
        }
        
        #stack-book-10 {
            background-color: #FFF;
            height: 15px;
            width: 110px;
            border: solid 5px #698CC1;
            border-left: none;
            border-right: none;
            margin-left: 0px;
            -webkit-transform: skew(10deg);
            -ms-transform: skew(10deg);
            transform: skew(10deg);
        }
        
        #stack-book-11 {
            background-color: #FCD57E;
            height: 0px;
            width: 110px;
            border: solid 4px #8E65A4;
            border-right: none;
            margin-left: 10px;
        }
        
        #stack-book-12 {
            background-color: #FCD57E;
            height: 0px;
            width: 110px;
            border: solid 4px #FAE7C7;
            border-right: none;
            margin-left: 5px;
        }
        
        #stack-book:hover #stack-book-1 {
            -webkit-animation: wiggle-1 0.2s infinite linear;
            animation: wiggle-1 0.2s infinite linear;
        }
        
        #stack-book:hover .stack-book-2 {
            -webkit-animation: wiggle-2 0.4s infinite linear;
            animation: wiggle-2 0.4s infinite linear;
        }
        
        #stack-book:hover .stack-book-3 {
            -webkit-animation: wiggle-3 0.5s infinite linear;
            animation: wiggle-3 0.5s infinite linear;
        }
        
        @-webkit-keyframes wiggle-1 {
            0% {
                -webkit-transform: rotate(5deg) translateY(-15px);
                transform: rotate(5deg) translateY(-15px);
            }
            50% {
                -webkit-transform: rotate(-5deg) translateY(-15px);
                transform: rotate(-5deg) translateY(-15px);
            }
            100% {
                -webkit-transform: rotate(5deg) translateY(-15px);
                transform: rotate(5deg) translateY(-15px);
            }
        }
        
        @keyframes wiggle-1 {
            0% {
                -webkit-transform: rotate(5deg) translateY(-15px);
                transform: rotate(5deg) translateY(-15px);
            }
            50% {
                -webkit-transform: rotate(-5deg) translateY(-15px);
                transform: rotate(-5deg) translateY(-15px);
            }
            100% {
                -webkit-transform: rotate(5deg) translateY(-15px);
                transform: rotate(5deg) translateY(-15px);
            }
        }
        
        @-webkit-keyframes wiggle-2 {
            0% {
                -webkit-transform: rotate(5deg) translateY(-10px);
                transform: rotate(5deg) translateY(-10px);
            }
            50% {
                -webkit-transform: rotate(-5deg) translateY(-10px);
                transform: rotate(-5deg) translateY(-10px);
            }
            100% {
                -webkit-transform: rotate(5deg) translateY(-10px);
                transform: rotate(5deg) translateY(-10px);
            }
        }
        
        @keyframes wiggle-2 {
            0% {
                -webkit-transform: rotate(5deg) translateY(-10px);
                transform: rotate(5deg) translateY(-10px);
            }
            50% {
                -webkit-transform: rotate(-5deg) translateY(-10px);
                transform: rotate(-5deg) translateY(-10px);
            }
            100% {
                -webkit-transform: rotate(5deg) translateY(-10px);
                transform: rotate(5deg) translateY(-10px);
            }
        }
        
        @-webkit-keyframes wiggle-3 {
            0% {
                -webkit-transform: rotate(5deg) translateY(-5px);
                transform: rotate(5deg) translateY(-5px);
            }
            50% {
                -webkit-transform: rotate(-5deg) translateY(-5px);
                transform: rotate(-5deg) translateY(-5px);
            }
            100% {
                -webkit-transform: rotate(5deg) translateY(-5px);
                transform: rotate(5deg) translateY(-5px);
            }
        }
        
        @keyframes wiggle-3 {
            0% {
                -webkit-transform: rotate(5deg) translateY(-5px);
                transform: rotate(5deg) translateY(-5px);
            }
            50% {
                -webkit-transform: rotate(-5deg) translateY(-5px);
                transform: rotate(-5deg) translateY(-5px);
            }
            100% {
                -webkit-transform: rotate(5deg) translateY(-5px);
                transform: rotate(5deg) translateY(-5px);
            }
        }
        /*END OF BOOK STACK*/
        /*BINDER STACK*/
        
        #stack-binder {
            width: auto;
            height: auto;
            display: inline-block;
            cursor: pointer;
            position: absolute;
            margin-top: 305px;
            margin-left: 290px;
            z-index: 100;
        }
        
        .stack-binder-right-bind {
            width: 120px;
            height: 35px;
            display: inline-block;
            position: relative;
        }
        
        .stack-binder-right-top,
        .stack-binder-right-bottom {
            width: 125px;
            height: 5px;
            position: absolute;
            -webkit-transform-origin: 100%;
            -ms-transform-origin: 100%;
            transform-origin: 100%;
        }
        
        .stack-binder-right-top {
            top: 0;
            -webkit-transform: rotate(-3deg);
            -ms-transform: rotate(-3deg);
            transform: rotate(-3deg);
        }
        
        .stack-binder-right-bottom {
            bottom: 0;
            -webkit-transform: rotate(3deg);
            -ms-transform: rotate(3deg);
            transform: rotate(3deg);
        }
        
        .stack-binder-left-paper,
        .stack-binder-right-paper {
            background-image: -webkit-gradient(linear, left top, left bottom, color-stop(50%, rgba(165, 216, 219, 1)), color-stop(50%, rgba(255, 255, 255, 1)));
            background-image: -webkit-linear-gradient(rgba(165, 216, 219, 1) 50%, rgba(255, 255, 255, 1) 50%);
            background-image: -o-linear-gradient(rgba(165, 216, 219, 1) 50%, rgba(255, 255, 255, 1) 50%);
            background-image: linear-gradient(rgba(165, 216, 219, 1) 50%, rgba(255, 255, 255, 1) 50%);
            background-size: 1px 2px;
            display: inline-block;
            margin-top: 4px;
            position: relative;
            height: 12px;
        }
        
        .stack-binder-left-paper {
            width: 100px;
            margin-left: 15px;
        }
        
        .stack-binder-right-paper {
            width: 95px;
            margin-left: -90px;
        }
        
        .stack-binder-left-ring,
        .stack-binder-right-ring {
            background-color: transparent;
            margin-top: 5px;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            border: solid 2px #FFF;
            display: inline-block;
            position: absolute;
        }
        
        .stack-binder-right-ring {
            margin-left: 95px
        }
        
        .stack-binder-left-bind {
            width: 120px;
            height: 35px;
            display: inline-block;
            position: relative;
        }
        
        .stack-binder-left-top,
        .stack-binder-left-bottom {
            position: absolute;
            width: 125px;
            height: 5px;
            -webkit-transform-origin: 0%;
            -ms-transform-origin: 0%;
            transform-origin: 0%;
        }
        
        .stack-binder-left-top {
            top: 0;
            -webkit-transform: rotate(3deg);
            -ms-transform: rotate(3deg);
            transform: rotate(3deg);
        }
        
        .stack-binder-left-bottom {
            bottom: 0;
            -webkit-transform: rotate(-3deg);
            -ms-transform: rotate(-3deg);
            transform: rotate(-3deg);
        }
        
        #stack-binder-1 {
            display: block;
            -webkit-transform: rotate(3deg);
            -ms-transform: rotate(3deg);
            transform: rotate(3deg);
            -webkit-transform-origin: 0%;
            -ms-transform-origin: 0%;
            transform-origin: 0%;
            position: relative;
            margin-bottom: -10px;
            margin-left: 20px;
            position: relative;
        }
        
        #stack-binder-1-bind {
            border-right: 8px solid #84A840;
        }
        
        .stack-binder-1-tb {
            background-color: #84A840;
        }
        
        #stack-binder-2,
        #stack-binder-3,
        #stack-binder-4 {
            display: block;
            -webkit-transform: rotate(3deg);
            -ms-transform: rotate(3deg);
            transform: rotate(3deg);
            -webkit-transform-origin: 0%;
            -ms-transform-origin: 0%;
            transform-origin: 0%;
            position: relative;
            margin-bottom: -10px;
        }
        
        #stack-binder-2 {
            margin-left: 15px;
        }
        
        #stack-binder-3 {
            margin-left: 10px;
        }
        
        #stack-binder-3-bind {
            border-right: 10px solid #EABBAE;
        }
        
        .stack-binder-3-tb {
            background-color: #EABBAE;
        }
        
        .stack-binder-4-bind {
            border-left: 15px solid #6787C0;
        }
        
        .stack-binder-4-tb {
            background-color: #6787C0;
        }
        
        #stack-binder:hover .stack-binder-right-top {
            -webkit-animation: flip-right 1s ease forwards;
            animation: flip-right 1s ease forwards;
        }
        
        #stack-binder:hover .stack-binder-left-top {
            -webkit-animation: flip-left 1s ease forwards;
            animation: flip-left 1s ease forwards;
        }
        
        #stack-binder:hover #stack-binder-1 {
            -webkit-animation: raise-1 0.5s ease forwards;
            animation: raise-1 0.5s ease forwards;
            -webkit-transform: rotate(-10deg);
            -ms-transform: rotate(-10deg);
            transform: rotate(-10deg);
        }
        
        #stack-binder:hover #stack-binder-2 {
            -webkit-animation: raise-2 0.5s ease forwards;
            animation: raise-2 0.5s ease forwards;
            -webkit-transform: rotate(-5deg);
            -ms-transform: rotate(-5deg);
            transform: rotate(-5deg);
        }
        
        #stack-binder:hover #stack-binder-3 {
            -webkit-animation: raise-3 0.5s ease forwards;
            animation: raise-3 0.5s ease forwards;
            -webkit-transform: rotate(-2deg);
            -ms-transform: rotate(-2deg);
            transform: rotate(-2deg);
        }
        
        @-webkit-keyframes raise-1 {
            100% {
                -webkit-transform: translateY(-40px);
                transform: translateY(-40px);
            }
        }
        
        @keyframes raise-1 {
            100% {
                -webkit-transform: translateY(-40px);
                transform: translateY(-40px);
            }
        }
        
        @-webkit-keyframes raise-2 {
            100% {
                -webkit-transform: translateY(-25px);
                transform: translateY(-25px);
            }
        }
        
        @keyframes raise-2 {
            100% {
                -webkit-transform: translateY(-25px);
                transform: translateY(-25px);
            }
        }
        
        @-webkit-keyframes raise-3 {
            100% {
                -webkit-transform: translateY(-5px);
                transform: translateY(-5px);
            }
        }
        
        @keyframes raise-3 {
            100% {
                -webkit-transform: translateY(-5px);
                transform: translateY(-5px);
            }
        }
        
        @-webkit-keyframes flip-right {
            100% {
                -webkit-transform: rotate(5deg);
                transform: rotate(5deg);
            }
        }
        
        @keyframes flip-right {
            100% {
                -webkit-transform: rotate(5deg);
                transform: rotate(5deg);
            }
        }
        
        @-webkit-keyframes flip-left {
            100% {
                -webkit-transform: rotate(-2deg);
                transform: rotate(-2deg);
            }
        }
        
        @keyframes flip-left {
            100% {
                -webkit-transform: rotate(-2deg);
                transform: rotate(-2deg);
            }
        }
        /*END OF BINDER STACK*/
        /*PENCIL HOLDER*/
        
        #pencil-holder {
            width: auto;
            height: auto;
            display: inline-block;
            position: absolute;
            margin-top: 400px;
            margin-left: 550px;
            z-index: 100;
        }
        
        #pencil-cup {
            display: inline-block;
            background-color: #FCD57E;
            width: 35px;
            height: 45px;
            position: absolute;
            z-index: 100;
            margin-top: 385px;
            margin-left: 530px;
            cursor: pointer;
            z-index: 110;
        }
        
        #pencil-cup:after {
            content: "";
            width: 20px;
            height: 20px;
            background-color: transparent;
            border-radius: 50%;
            border: 5px solid #FCD57E;
            -webkit-transform: rotate(90deg);
            -ms-transform: rotate(90deg);
            transform: rotate(90deg);
            display: inline-block;
            position: relative;
            -webkit-transform: translate(40px, 5px);
            -ms-transform: translate(40px, 5px);
            transform: translate(40px, 5px);
        }
        
        #heart {
            display: inline-block;
            position: relative;
            width: 12px;
            height: 20px;
            margin-left: -33px;
            margin-top: 12px;
            z-index: 100;
        }
        
        #heart:before,
        #heart:after {
            position: absolute;
            content: "";
            left: 50px;
            top: 0;
            width: 12px;
            height: 18px;
            background: #F47164;
            border-radius: 50px 50px 0 0;
            -webkit-transform: rotate(-45deg);
            -ms-transform: rotate(-45deg);
            transform: rotate(-45deg);
            -webkit-transform-origin: 0 100%;
            -ms-transform-origin: 0 100%;
            transform-origin: 0 100%;
            z-index: 100;
        }
        
        #heart:after {
            margin-left: 38px;
            left: 0;
            -webkit-transform: rotate(45deg);
            -ms-transform: rotate(45deg);
            transform: rotate(45deg);
            -webkit-transform-origin: 100% 100%;
            -ms-transform-origin: 100% 100%;
            transform-origin: 100% 100%;
        }
        
        #ruler {
            display: inline-block;
            width: 80px;
            height: 13px;
            margin-left: 7px;
            background: -webkit-repeating-linear-gradient( left, #3E3F4B, #3E3F4B 1px, #FAE7C7 1px, #FAE7C7 5px);
            background: -o-repeating-linear-gradient( left, #3E3F4B, #3E3F4B 1px, #FAE7C7 1px, #FAE7C7 5px);
            background: repeating-linear-gradient( to right, #3E3F4B, #3E3F4B 1px, #FAE7C7 1px, #FAE7C7 5px);
            -webkit-transform: rotate(-80deg);
            -ms-transform: rotate(-80deg);
            transform: rotate(-80deg);
            -webkit-transform-origin: 0 100%;
            -ms-transform-origin: 0 100%;
            transform-origin: 0 100%;
        }
        
        #ruler-inner {
            width: 80px;
            height: 7px;
            background-color: #FAE7C7;
        }
        
        #ruler:hover {
            -webkit-animation: ruler-raise 0.5s ease forwards;
            animation: ruler-raise 0.5s ease forwards;
            cursor: pointer;
        }
        
        @-webkit-keyframes ruler-raise {
            100% {
                -webkit-transform: translate(10px, -40px) rotate(10deg) rotate(-80deg);
                transform: translate(10px, -40px) rotate(10deg) rotate(-80deg);
            }
        }
        
        @keyframes ruler-raise {
            100% {
                -webkit-transform: translate(10px, -40px) rotate(10deg) rotate(-80deg);
                transform: translate(10px, -40px) rotate(10deg) rotate(-80deg);
            }
        }
        
        #pencil-1,
        #pencil-2 {
            -webkit-transform-origin: 0%;
            -ms-transform-origin: 0%;
            transform-origin: 0%;
            margin-top: -60px;
            border-bottom: solid 8px #EABBAE;
            position: absolute;
            width: 8px;
            height: 60px;
        }
        
        #pencil-1 {
            background: -webkit-repeating-linear-gradient( left, #f6ba52, #f6ba52 2px, #F47164 2px, #F47164 4px);
            background: -o-repeating-linear-gradient( left, #f6ba52, #f6ba52 2px, #F47164 2px, #F47164 4px);
            background: repeating-linear-gradient( to right, #f6ba52, #f6ba52 2px, #F47164 2px, #F47164 4px);
            margin-left: -15px;
            -webkit-transform: rotate(-8deg);
            -ms-transform: rotate(-8deg);
            transform: rotate(-8deg);
        }
        
        #pencil-2 {
            background: -webkit-repeating-linear-gradient( left, #84A840, #84A840 2px, #6787C0 2px, #6787C0 4px);
            background: -o-repeating-linear-gradient( left, #84A840, #84A840 2px, #6787C0 2px, #6787C0 4px);
            background: repeating-linear-gradient( to right, #84A840, #84A840 2px, #6787C0 2px, #6787C0 4px);
            margin-left: -5px;
            -webkit-transform: rotate(-2deg);
            -ms-transform: rotate(-2deg);
            transform: rotate(-2deg);
        }
        
        .pencil-tip,
        .pencil-tip-top {
            position: relative;
            margin-top: -10px;
            width: 0;
            height: 0;
        }
        
        .pencil-tip {
            border-bottom: 10px solid #FAE7C7;
            border-left: 4px solid transparent;
            border-right: 4px solid transparent;
        }
        
        .pencil-tip-top {
            margin-left: -1.5px;
            border-bottom: 4px solid #3E3F4B;
            border-left: 1.5px solid transparent;
            border-right: 1.5px solid transparent;
        }
        
        #pencil-1:hover {
            -webkit-animation: pencil-raise 0.8s ease forwards;
            animation: pencil-raise 0.8s ease forwards;
            cursor: pointer;
            -webkit-transform-origin: 0%;
            -ms-transform-origin: 0%;
            transform-origin: 0%;
        }
        
        #pencil-2:hover {
            -webkit-animation: pencil-raise-2 0.8s ease forwards;
            animation: pencil-raise-2 0.8s ease forwards;
            cursor: pointer;
            -webkit-transform: translateY(-5px);
            -ms-transform: translateY(-5px);
            transform: translateY(-5px)
        }
        
        @-webkit-keyframes pencil-raise {
            100% {
                -webkit-transform: translate(-10px, -50px) rotate(-10deg);
                transform: translate(-10px, -50px) rotate(-10deg);
            }
        }
        
        @keyframes pencil-raise {
            100% {
                -webkit-transform: translate(-10px, -50px) rotate(-10deg);
                transform: translate(-10px, -50px) rotate(-10deg);
            }
        }
        
        @-webkit-keyframes pencil-raise-2 {
            100% {
                -webkit-transform: translate(-2px, -60px);
                transform: translate(-2px, -60px);
            }
        }
        
        @keyframes pencil-raise-2 {
            100% {
                -webkit-transform: translate(-2px, -60px);
                transform: translate(-2px, -60px);
            }
        }
        
        #pencil-cup:hover #heart {
            -webkit-animation: heartbeat 0.5s infinite ease;
            animation: heartbeat 0.5s infinite ease;
            cursor: pointer;
        }
        
        @-webkit-keyframes heartbeat {
            100% {
                -webkit-transform: scale(1.2) translate(-7px, 0px);
                transform: scale(1.2) translate(-7px, 0px);
            }
        }
        
        @keyframes heartbeat {
            100% {
                -webkit-transform: scale(1.2) translate(-7px, 0px);
                transform: scale(1.2) translate(-7px, 0px);
            }
        }
        /*END OF PENCIL HOLDER*/
        /*COFFEE CUP*/
        
        #coffee-cup {
            width: auto;
            height: auto;
            display: inline-block;
            position: absolute;
            margin-top: 375px;
            margin-left: 460px;
            z-index: 100;
        }
        
        #coffee-cup-bottom {
            border-top: 55px solid #FFF;
            border-left: 5px solid transparent;
            border-right: 5px solid transparent;
            height: 0;
            width: 25px;
            position: relative;
        }
        
        #coffee-cup-holder {
            border-top: 20px solid #EABBAE;
            border-left: 2px solid transparent;
            border-right: 2px solid transparent;
            height: 0;
            width: 31px;
            position: relative;
            z-index: 100;
            margin-top: -40px;
            margin-left: -5px;
        }
        
        #coffee-cup-holder:before {
            content: "";
            position: absolute;
            left: 1px;
            bottom: -1px;
            height: 1px;
            width: 29px;
            border-bottom: 1px solid #A5D8DB;
        }
        
        #coffee-cup-logo {
            background-color: #84A840;
            width: 15px;
            height: 15px;
            border-radius: 50%;
            position: relative;
            margin-top: -17px;
            margin-left: 8px;
        }
        
        #coffee-cup-top {
            border-bottom: 10px solid #FFF;
            border-left: 5px solid transparent;
            border-right: 5px solid transparent;
            height: 0;
            width: 25px;
            margin-top: -10px;
            position: relative;
        }
        
        #coffee-cup-rim {
            background-color: #FFF;
            width: 41px;
            height: 3px;
            margin-left: -8px;
            margin-top: 10px;
            position: absolute;
            z-index: 100;
            border-bottom: 1px solid #A5D8DB;
            border-top: 0.5px solid #A5D8DB;
        }
        
        #coffee-cup:hover #coffee-cup-top {
            cursor: pointer;
            -webkit-animation: lid 2s ease infinite;
            animation: lid 2s ease infinite;
            -webkit-transform-origin: 100%;
            -ms-transform-origin: 100%;
            transform-origin: 100%;
        }
        
        #coffee-cup:hover {
            cursor: pointer;
            -webkit-animation: shake 1s ease infinite;
            animation: shake 1s ease infinite;
            -webkit-transform-origin: 100%;
            -ms-transform-origin: 100%;
            transform-origin: 100%;
        }
        
        @-webkit-keyframes lid {
            0% {
                -webkit-transform: rotate(0deg) translate(0px, -0px);
                transform: rotate(0deg) translate(0px, -0px);
            }
            50% {
                -webkit-transform: rotate(30deg) translate(5px, -8px);
                transform: rotate(30deg) translate(5px, -8px);
            }
            100% {
                -webkit-transform: rotate(0deg) translate(0px, -0px);
                transform: rotate(0deg) translate(0px, -0px);
            }
        }
        
        @keyframes lid {
            0% {
                -webkit-transform: rotate(0deg) translate(0px, -0px);
                transform: rotate(0deg) translate(0px, -0px);
            }
            50% {
                -webkit-transform: rotate(30deg) translate(5px, -8px);
                transform: rotate(30deg) translate(5px, -8px);
            }
            100% {
                -webkit-transform: rotate(0deg) translate(0px, -0px);
                transform: rotate(0deg) translate(0px, -0px);
            }
        }
        
        @-webkit-keyframes shake {
            0% {
                -webkit-transform: translate(2px, -5px) rotate(0deg);
                transform: translate(2px, -5px) rotate(0deg);
            }
            10% {
                -webkit-transform: translate(-1px, -3px) rotate(-1deg);
                transform: translate(-1px, -3px) rotate(-1deg);
            }
            20% {
                -webkit-transform: translate(-3px, -4px) rotate(1deg);
                transform: translate(-3px, -4px) rotate(1deg);
            }
            30% {
                -webkit-transform: translate(0px, -5px) rotate(0deg);
                transform: translate(0px, -5px) rotate(0deg);
            }
            40% {
                -webkit-transform: translate(1px, -3px) rotate(1deg);
                transform: translate(1px, -3px) rotate(1deg);
            }
            50% {
                -webkit-transform: translate(-1px, -4px) rotate(-1deg);
                transform: translate(-1px, -4px) rotate(-1deg);
            }
            60% {
                -webkit-transform: translate(-3px, -5px) rotate(0deg);
                transform: translate(-3px, -5px) rotate(0deg);
            }
            70% {
                -webkit-transform: translate(2px, -2px) rotate(-1deg);
                transform: translate(2px, -2px) rotate(-1deg);
            }
            80% {
                -webkit-transform: translate(-1px, -3px) rotate(1deg);
                transform: translate(-1px, -3px) rotate(1deg);
            }
            90% {
                -webkit-transform: translate(2px, -5px) rotate(0deg);
                transform: translate(2px, -5px) rotate(0deg);
            }
            100% {
                -webkit-transform: translate(1px, -2px) rotate(-1deg);
                transform: translate(1px, -2px) rotate(-1deg);
            }
        }
        
        @keyframes shake {
            0% {
                -webkit-transform: translate(2px, -5px) rotate(0deg);
                transform: translate(2px, -5px) rotate(0deg);
            }
            10% {
                -webkit-transform: translate(-1px, -3px) rotate(-1deg);
                transform: translate(-1px, -3px) rotate(-1deg);
            }
            20% {
                -webkit-transform: translate(-3px, -4px) rotate(1deg);
                transform: translate(-3px, -4px) rotate(1deg);
            }
            30% {
                -webkit-transform: translate(0px, -5px) rotate(0deg);
                transform: translate(0px, -5px) rotate(0deg);
            }
            40% {
                -webkit-transform: translate(1px, -3px) rotate(1deg);
                transform: translate(1px, -3px) rotate(1deg);
            }
            50% {
                -webkit-transform: translate(-1px, -4px) rotate(-1deg);
                transform: translate(-1px, -4px) rotate(-1deg);
            }
            60% {
                -webkit-transform: translate(-3px, -5px) rotate(0deg);
                transform: translate(-3px, -5px) rotate(0deg);
            }
            70% {
                -webkit-transform: translate(2px, -2px) rotate(-1deg);
                transform: translate(2px, -2px) rotate(-1deg);
            }
            80% {
                -webkit-transform: translate(-1px, -3px) rotate(1deg);
                transform: translate(-1px, -3px) rotate(1deg);
            }
            90% {
                -webkit-transform: translate(2px, -5px) rotate(0deg);
                transform: translate(2px, -5px) rotate(0deg);
            }
            100% {
                -webkit-transform: translate(1px, -2px) rotate(-1deg);
                transform: translate(1px, -2px) rotate(-1deg);
            }
        }
        
        p.cup {
            position: absolute;
            display: inline-block;
            font-family: "Pacifico", cursive;
            font-size: 8px;
            color: #3E3F4B;
            margin-left: 2px;
            margin-top: -28px;
            -webkit-transform: rotate(-15deg);
            -ms-transform: rotate(-15deg);
            transform: rotate(-15deg);
        }
        /*END OF COFFEE CUP*/
        /*TAKE-OUT*/
        
        #take-out {
            width: auto;
            height: auto;
            display: inline-block;
            position: absolute;
            margin-top: 313px;
            margin-left: 800px;
            cursor: pointer;
        }
        
        #take-out-box {
            position: absolute;
            z-index: 100;
        }
        
        #take-out-box-top {
            border-bottom: 20px solid #C0E0E3;
            border-left: 10px solid transparent;
            border-right: 10px solid transparent;
            height: 0;
            width: 32px;
            margin-top: -20px;
            position: relative;
        }
        
        #take-out-box-bottom {
            border-top: 50px solid #FFF;
            border-left: 8px solid transparent;
            border-right: 8px solid transparent;
            height: 0;
            width: 35px;
            position: relative;
        }
        
        #take-out-box-bottom-back {
            background-color: #C0E0E3;
            width: 15px;
            height: 50px;
            position: relative;
            margin-left: 47px;
            margin-top: -50px;
            -webkit-transform: skew(-9deg, 0deg);
            -ms-transform: skew(-9deg, 0deg);
            transform: skew(-9deg, 0deg);
        }
        
        #chopsticks {
            width: auto;
            height: auto;
            display: inline-block;
            position: relative;
            margin-top: -40px;
            margin-left: 40px;
            z-index: 50;
        }
        
        #chopsticks-1,
        #chopsticks-2 {
            position: relative;
            background-color: #F47164;
            height: 70px;
            width: 3px;
            display: inline-block;
        }
        
        #chopsticks-1 {
            -webkit-transform: rotate(15deg);
            -ms-transform: rotate(15deg);
            transform: rotate(15deg);
        }
        
        #chopsticks-2 {
            -webkit-transform: rotate(30deg);
            -ms-transform: rotate(30deg);
            transform: rotate(30deg);
            margin-left: 10px;
        }
        
        #take-out:hover #chopsticks-1 {
            -webkit-animation: chopstick-raise 1s ease forwards;
            animation: chopstick-raise 1s ease forwards;
        }
        
        #take-out:hover #chopsticks-2 {
            -webkit-animation: chopstick-raise-2 1s ease forwards;
            animation: chopstick-raise-2 1s ease forwards;
        }
        
        @-webkit-keyframes chopstick-raise {
            20% {
                -webkit-transform: translate(20px, -55px) rotate(50deg);
                transform: translate(20px, -55px) rotate(50deg);
            }
            50% {
                -webkit-transform: translate(20px, -55px) rotate(30deg);
                transform: translate(20px, -55px) rotate(30deg);
            }
            65% {
                -webkit-transform: translate(20px, -55px) rotate(50deg);
                transform: translate(20px, -55px) rotate(50deg);
            }
            80% {
                -webkit-transform: translate(20px, -55px) rotate(30deg);
                transform: translate(20px, -55px) rotate(30deg);
            }
            100% {
                -webkit-transform: translate(0px, 0px) rotate(15deg);
                transform: translate(0px, 0px) rotate(15deg);
            }
        }
        
        @keyframes chopstick-raise {
            20% {
                -webkit-transform: translate(20px, -55px) rotate(50deg);
                transform: translate(20px, -55px) rotate(50deg);
            }
            50% {
                -webkit-transform: translate(20px, -55px) rotate(30deg);
                transform: translate(20px, -55px) rotate(30deg);
            }
            65% {
                -webkit-transform: translate(20px, -55px) rotate(50deg);
                transform: translate(20px, -55px) rotate(50deg);
            }
            80% {
                -webkit-transform: translate(20px, -55px) rotate(30deg);
                transform: translate(20px, -55px) rotate(30deg);
            }
            100% {
                -webkit-transform: translate(0px, 0px) rotate(15deg);
                transform: translate(0px, 0px) rotate(15deg);
            }
        }
        
        @-webkit-keyframes chopstick-raise-2 {
            20% {
                -webkit-transform: translate(10px, -50px) rotate(35deg);
                transform: translate(10px, -50px) rotate(35deg);
            }
            50% {
                -webkit-transform: translate(10px, -50px) rotate(40deg);
                transform: translate(10px, -50px) rotate(40deg);
            }
            65% {
                -webkit-transform: translate(10px, -50px) rotate(35deg);
                transform: translate(10px, -50px) rotate(35deg);
            }
            80% {
                -webkit-transform: translate(10px, -50px) rotate(40deg);
                transform: translate(10px, -50px) rotate(40deg);
            }
            100% {
                -webkit-transform: translate(0px, 0px) rotate(30deg);
                transform: translate(0px, 0px) rotate(30deg);
            }
        }
        
        @keyframes chopstick-raise-2 {
            20% {
                -webkit-transform: translate(10px, -50px) rotate(35deg);
                transform: translate(10px, -50px) rotate(35deg);
            }
            50% {
                -webkit-transform: translate(10px, -50px) rotate(40deg);
                transform: translate(10px, -50px) rotate(40deg);
            }
            65% {
                -webkit-transform: translate(10px, -50px) rotate(35deg);
                transform: translate(10px, -50px) rotate(35deg);
            }
            80% {
                -webkit-transform: translate(10px, -50px) rotate(40deg);
                transform: translate(10px, -50px) rotate(40deg);
            }
            100% {
                -webkit-transform: translate(0px, 0px) rotate(30deg);
                transform: translate(0px, 0px) rotate(30deg);
            }
        }
        
        #take-out:hover #take-out-box {
            -webkit-animation: bounce 1s ease forwards;
            animation: bounce 1s ease forwards;
        }
        
        @-webkit-keyframes bounce {
            0% {
                -webkit-transform: rotateX(0deg);
                transform: rotateX(0deg);
            }
            20% {
                -webkit-transform: rotateX(-30deg) translate(0px, 3px);
                transform: rotateX(-30deg) translate(0px, 3px);
            }
            100% {
                -webkit-transform: rotateX(0deg);
                transform: rotateX(0deg);
            }
        }
        
        @keyframes bounce {
            0% {
                -webkit-transform: rotateX(0deg);
                transform: rotateX(0deg);
            }
            20% {
                -webkit-transform: rotateX(-30deg) translate(0px, 3px);
                transform: rotateX(-30deg) translate(0px, 3px);
            }
            100% {
                -webkit-transform: rotateX(0deg);
                transform: rotateX(0deg);
            }
        }
        
        #take-out-box-handle,
        #take-out-box-handle-dot {
            background-color: #3E3F4B;
            position: absolute;
            z-index: 100;
        }
        
        #take-out-box-handle {
            height: 35px;
            margin-top: -45px;
            width: 3px;
            -webkit-transform: rotate(45deg);
            -ms-transform: rotate(45deg);
            transform: rotate(45deg);
            display: inline-block;
            margin-left: 3px;
        }
        
        #take-out-box-handle-dot {
            width: 5px;
            height: 5px;
            border-radius: 50%;
            margin-top: -2px;
            margin-left: -1px;
        }
        
        p.box {
            position: relative;
            display: inline-block;
            font-family: "Permanent Marker", cursive;
            font-size: 9px;
            text-align: center;
            line-height: 10px;
            color: #F47164;
            margin-left: -40px;
            margin-top: 20px;
            -webkit-transform: rotate(10deg);
            -ms-transform: rotate(10deg);
            transform: rotate(10deg);
            opacity: 0.8;
        }
        /*END OF TAKE-OUT*/
        /*COMPUTER*/
        
        #computer {
            width: auto;
            height: auto;
            display: inline-block;
            position: absolute;
            margin-top: 180px;
            margin-left: 520px;
            z-index: 10;
        }
        
        #computer-back {
            background-color: #D9EDEE;
            width: 250px;
            height: 160px;
            border-radius: 20px;
            position: relative;
            margin-left: 20px;
        }
        
        #computer-side {
            background-color: #FFF;
            width: 50px;
            height: 160px;
            border-radius: 20px 0px 0px 20px;
            position: relative;
            margin-top: 35px;
        }
        
        #computer-logo {
            position: relative;
            background-color: #BFDFE4;
            width: 30px;
            height: 26px;
            border-radius: 50%;
            margin: auto;
            -webkit-transform: translateY(50px);
            -ms-transform: translateY(50px);
            transform: translateY(50px);
        }
        
        #computer-logo-bite {
            position: absolute;
            background-color: #D9EDEE;
            width: 15px;
            height: 13px;
            border-radius: 50%;
            -webkit-transform: translate(105px, 30px);
            -ms-transform: translate(105px, 30px);
            transform: translate(105px, 30px);
        }
        
        #computer-logo-stem {
            position: absolute;
            background-color: #BFDFE4;
            width: 4px;
            height: 10px;
            -webkit-transform: translate(120px, 15px) rotate(-15deg);
            -ms-transform: translate(120px, 15px) rotate(-15deg);
            transform: translate(120px, 15px) rotate(-15deg);
        }
        
        #computer-logo-leaf {
            position: absolute;
            background-color: #BFDFE4;
            width: 7px;
            height: 15px;
            border-radius: 50%;
            -webkit-transform: translate(126px, 15px) rotate(30deg);
            -ms-transform: translate(126px, 15px) rotate(30deg);
            transform: translate(126px, 15px) rotate(30deg);
        }
        
        #computer-stand {
            position: relative;
            margin-top: -65px;
            margin-left: 125px;
            border-bottom: 120px solid #6686BF;
            border-right: 20px solid transparent;
            border-radius: 0px 0px 20px 0px;
            height: 0;
            width: 50px;
            -webkit-transform: skewX(5deg);
            -ms-transform: skewX(5deg);
            transform: skewX(5deg);
            cursor: pointer;
        }
        
        #computer-stand-hole {
            position: relative;
            background-color: #BFDFE4;
            width: 25px;
            height: 25px;
            margin-left: 15px;
            margin-bottom: -15px;
            display: inline-block;
            border-radius: 50%;
        }
        
        #computer-stand-hole:after {
            content: "";
            position: absolute;
            background-color: #A5D8DB;
            height: 15px;
            width: 25px;
            border-radius: 0 0 90px 90px;
            bottom: 0;
        }
        
        #computer-stand-shadow {
            position: relative;
            width: 0;
            height: 0;
            border-left: 15px solid transparent;
            border-right: 1px solid transparent;
            border-bottom: 65px solid #BFDFE4;
            margin-left: -16px;
            display: inline-block;
        }
        
        #computer-stand-bottom {
            position: relative;
            margin-top: -10px;
            margin-left: 80px;
            background-color: #6686BF;
            width: 55px;
            height: 10px;
            cursor: pointer;
        }
        
        #computer-stand-curve {
            position: relative;
            margin-top: -15px;
            margin-left: 75px;
            background-color: #A5D8DB;
            border-radius: 0px 0px 15px 0px;
            width: 55px;
            height: 10px;
            -webkit-transform: skewX(5deg);
            -ms-transform: skewX(5deg);
            transform: skewX(5deg);
        }
        
        #computer-cable {
            display: inline-block;
            position: relative;
            height: 55px;
            width: 60px;
            background: transparent;
            border-radius: 0px 0px 0px 370px/280px;
            border: solid 3px #D9EDEE;
            border-top: none;
            border-right: none;
            margin: 20px;
            margin-top: -5px;
            margin-left: 30px;
        }
        
        #computer:hover #computer-side {
            -webkit-animation: computer-adjust 2s ease infinite;
            animation: computer-adjust 2s ease infinite;
            cursor: pointer;
        }
        
        @-webkit-keyframes computer-adjust {
            50% {
                -webkit-transform: skewX(8deg);
                transform: skewX(8deg);
            }
            100% {
                -webkit-transform: skewX(0deg);
                transform: skewX(0deg);
            }
        }
        
        @keyframes computer-adjust {
            50% {
                -webkit-transform: skewX(8deg);
                transform: skewX(8deg);
            }
            100% {
                -webkit-transform: skewX(0deg);
                transform: skewX(0deg);
            }
        }
        /*END OF COMPUTER*/
        /*BOOK STACK SMALL*/
        
        #stack-book-small {
            width: 135px;
            height: auto;
            display: inline-block;
            margin-top: 355px;
            margin-left: 750px;
            position: absolute;
            -webkit-transform: scale(0.8);
            -ms-transform: scale(0.8);
            transform: scale(0.8);
            z-index: 100;
        }
        
        #stack-book-small:hover {
            -webkit-animation: book-stack-shift 0.5s ease forwards;
            animation: book-stack-shift 0.5s ease forwards;
            cursor: pointer;
        }
        
        @-webkit-keyframes book-stack-shift {
            40% {
                -webkit-transform: skewX(3deg) scale(0.8) translate(-3px);
                transform: skewX(3deg) scale(0.8) translate(-3px);
            }
            60% {
                -webkit-transform: skewX(-3deg) scale(0.8) translate(3px);
                transform: skewX(-3deg) scale(0.8) translate(3px);
            }
            100% {
                -webkit-transform: skewX(0deg) scale(0.8);
                transform: skewX(0deg) scale(0.8);
            }
        }
        
        @keyframes book-stack-shift {
            40% {
                -webkit-transform: skewX(3deg) scale(0.8) translate(-3px);
                transform: skewX(3deg) scale(0.8) translate(-3px);
            }
            60% {
                -webkit-transform: skewX(-3deg) scale(0.8) translate(3px);
                transform: skewX(-3deg) scale(0.8) translate(3px);
            }
            100% {
                -webkit-transform: skewX(0deg) scale(0.8);
                transform: skewX(0deg) scale(0.8);
            }
        }
        /*END OF BOOK STACK SMALL*/
        /*CHAIR*/
        
        #chair {
            width: auto;
            height: auto;
            display: inline-block;
            margin-top: 540px;
            margin-left: 410px;
            position: absolute;
            z-index: 5;
        }
        
        #chair-seat,
        #chair-arm-left,
        #chair-arm-right {
            background-color: #8E65A4;
        }
        
        #chair-seat {
            position: relative;
            width: 210px;
            height: 30px;
            border-radius: 25px;
        }
        
        #chair-arm-left,
        #chair-arm-right {
            position: absolute;
            width: 50px;
            height: 90px;
            bottom: 0;
            border-radius: 20px;
            z-index: 10;
        }
        
        #chair-arm-left {
            left: 0;
        }
        
        #chair-arm-right {
            right: 0;
        }
        
        #chair-back,
        #chair-spine,
        #chair-pole {
            position: absolute;
            background-color: #4F395C;
        }
        
        #chair-back {
            width: 150px;
            height: 200px;
            bottom: 0;
            margin-left: 30px;
            border-radius: 20px;
            z-index: 1;
            margin-bottom: 50px;
            pointer-events: none;
            z-index: 0;
        }
        
        #chair-spine {
            width: 100px;
            height: 20px;
            bottom: 0;
            margin-left: 55px;
            margin-bottom: 30px;
        }
        
        #chair-pole {
            width: 30px;
            height: 50px;
            top: 0;
            margin-left: 90px;
            margin-top: 30px;
        }
        
        #chair-rod {
            position: relative;
            background-color: #4F395C;
            width: 15px;
            height: 40px;
            margin-left: 8px;
            margin-top: 50px;
        }
        
        #chair-legs {
            position: relative;
            margin-top: 90px;
            display: inline-block;
        }
        
        #chair-leg-middle {
            border-top: 35px solid #4F395C;
            margin-left: 20px;
            margin-bottom: 23px;
        }
        
        #chair-leg-middle,
        #chair-leg-left,
        #chair-leg-right {
            position: relative;
            border-left: 5px solid transparent;
            border-right: 5px solid transparent;
            display: inline-block;
            height: 0;
            width: 5px;
        }
        
        #chair-leg-left,
        #chair-leg-right {
            -webkit-transform-origin: 100%;
            -ms-transform-origin: 100%;
            transform-origin: 100%;
            border-top: 75px solid #4F395C;
        }
        
        #chair-leg-left {
            margin-left: 60px;
            -webkit-transform: rotate(70deg);
            -ms-transform: rotate(70deg);
            transform: rotate(70deg)
        }
        
        #chair-leg-right {
            -webkit-transform: rotate(-70deg);
            -ms-transform: rotate(-70deg);
            transform: rotate(-70deg);
            margin-left: 10px;
            margin-bottom: 14px;
        }
        
        #left-wheel,
        #middle-wheel,
        #right-wheel {
            position: relative;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background-color: #4F395C;
        }
        
        #left-wheel {
            -webkit-transform: translate(0px, -5px);
            -ms-transform: translate(0px, -5px);
            transform: translate(0px, -5px);
        }
        
        #middle-wheel {
            -webkit-transform: translate(-7px, -8px);
            -ms-transform: translate(-7px, -8px);
            transform: translate(-7px, -8px);
        }
        
        #right-wheel {
            -webkit-transform: translate(-15px, -5px);
            -ms-transform: translate(-15px, -5px);
            transform: translate(-15px, -5px);
        }
        
        #chair-seat.animated {
            -webkit-animation: chair 2s ease-out;
            animation: chair 2s ease-out;
            cursor: pointer;
        }
        
        @-webkit-keyframes chair {
            60% {
                -webkit-transform: translateX(-180px) rotate(5deg);
                transform: translateX(-180px) rotate(5deg);
            }
            70% {
                -webkit-transform: translateX(-190px);
                transform: translateX(-190px);
            }
            80% {
                -webkit-transform: translateX(-200px) rotate(-3deg);
                transform: translateX(-200px) rotate(-3deg);
            }
            90% {
                -webkit-transform: translateX(0px) rotate(-8deg);
                transform: translateX(0px) rotate(-8deg);
            }
            100% {
                -webkit-transform: translateX(0px) rotate(0deg);
                transform: translateX(0px) rotate(0deg);
            }
        }
        
        @keyframes chair {
            60% {
                -webkit-transform: translateX(-180px) rotate(5deg);
                transform: translateX(-180px) rotate(5deg);
            }
            70% {
                -webkit-transform: translateX(-190px);
                transform: translateX(-190px);
            }
            80% {
                -webkit-transform: translateX(-200px) rotate(-3deg);
                transform: translateX(-200px) rotate(-3deg);
            }
            90% {
                -webkit-transform: translateX(0px) rotate(-8deg);
                transform: translateX(0px) rotate(-8deg);
            }
            100% {
                -webkit-transform: translateX(0px) rotate(0deg);
                transform: translateX(0px) rotate(0deg);
            }
        }
        /*END OF CHAIR*/
        /*SHELF 1*/
        
        #shelf-area {
            width: auto;
            height: auto;
            display: inline-block;
            margin-top: 90px;
            margin-left: 550px;
            position: absolute;
            z-index: 1;
        }
        
        #shelf-1,
        #shelf-2 {
            position: relative;
            display: inline-block;
            background-color: #F47164;
            width: 170px;
            height: 10px;
        }
        
        #shelf-2 {
            margin-bottom: -80px;
        }
        
        #shelf-1-book-1,
        #shelf-1-book-2 {
            position: relative;
            width: 18px;
            height: 70px;
            margin-top: -70px;
        }
        
        #shelf-1-book-1 {
            background-color: #84A840;
            margin-left: 15px;
        }
        
        #shelf-1-book-2 {
            background-color: #6686BF;
            margin-left: 35px;
        }
        
        #shelf-1-book-1-line-1,
        #shelf-1-book-2-line-1 {
            position: absolute;
            width: 18px;
            height: 3px;
            margin-top: 5px;
        }
        
        #shelf-1-book-1-line-1 {
            background-color: #FCD57E;
        }
        
        #shelf-1-book-2-line-1 {
            background-color: #EABBAE;
        }
        
        #shelf-1-book-1-line-2,
        #shelf-1-book-2-line-2 {
            position: absolute;
            background-color: #FFF;
            width: 10px;
            height: 25px;
            margin-top: 12px;
            margin-left: 4px;
        }
        
        #shelf-1-book-1-line-3,
        #shelf-1-book-2-line-3 {
            position: absolute;
            width: 18px;
            height: 4px;
            margin-top: 45px;
        }
        
        #shelf-1-book-1-line-3 {
            background-color: #FCD57E;
        }
        
        #shelf-1-book-2-line-3 {
            background-color: #EABBAE;
        }
        
        #shelf-1-book-3,
        #shelf-1-book-4 {
            position: relative;
            width: 10px;
            height: 60px;
            margin-top: -61px;
            -webkit-transform-origin: bottom;
            -ms-transform-origin: bottom;
            transform-origin: bottom;
        }
        
        #shelf-1-book-3 {
            background-color: #EABBAE;
            margin-left: 69px;
            -webkit-transform: rotate(-15deg);
            -ms-transform: rotate(-15deg);
            transform: rotate(-15deg);
        }
        
        #shelf-1-book-4 {
            background-color: #FCD57E;
            margin-left: 96px;
            -webkit-transform: rotate(-30deg);
            -ms-transform: rotate(-30deg);
            transform: rotate(-30deg);
        }
        
        #shelf-1-book-1:hover,
        #shelf-1-book-2:hover {
            -webkit-animation: shelf-book-raise 0.8s ease-in forwards;
            animation: shelf-book-raise 0.8s ease-in forwards;
            cursor: pointer;
        }
        
        #shelf-1-book-3:hover {
            -webkit-animation: shelf-book-shift-1 0.4s alternate infinite;
            animation: shelf-book-shift-1 0.4s alternate infinite;
            cursor: pointer;
        }
        
        #shelf-1-book-4:hover {
            -webkit-animation: shelf-book-shift-2 0.3s ease-in infinite;
            animation: shelf-book-shift-2 0.3s ease-in infinite;
            -webkit-transform-origin: bottom;
            -ms-transform-origin: bottom;
            transform-origin: bottom;
            cursor: pointer;
        }
        
        @-webkit-keyframes shelf-book-shift-2 {
            20% {
                -webkit-transform: rotate(-20deg);
                transform: rotate(-20deg);
            }
            50% {
                -webkit-transform: rotate(-25deg);
                transform: rotate(-25deg);
            }
            70% {
                -webkit-transform: rotate(-23deg);
                transform: rotate(-23deg);
            }
            100% {
                -webkit-transform: rotate(-25deg);
                transform: rotate(-25deg);
            }
        }
        
        @keyframes shelf-book-shift-2 {
            20% {
                -webkit-transform: rotate(-20deg);
                transform: rotate(-20deg);
            }
            50% {
                -webkit-transform: rotate(-25deg);
                transform: rotate(-25deg);
            }
            70% {
                -webkit-transform: rotate(-23deg);
                transform: rotate(-23deg);
            }
            100% {
                -webkit-transform: rotate(-25deg);
                transform: rotate(-25deg);
            }
        }
        
        @-webkit-keyframes shelf-book-shift-1 {
            100% {
                -webkit-transform: translate(-14px);
                transform: translate(-14px);
            }
        }
        
        @keyframes shelf-book-shift-1 {
            100% {
                -webkit-transform: translate(-14px);
                transform: translate(-14px);
            }
        }
        
        @-webkit-keyframes shelf-book-raise {
            50% {
                -webkit-transform: translateY(-10px);
                transform: translateY(-10px);
            }
            100% {
                -webkit-transform: translateY(0px);
                transform: translateY(0px);
            }
        }
        
        @keyframes shelf-book-raise {
            50% {
                -webkit-transform: translateY(-10px);
                transform: translateY(-10px);
            }
            100% {
                -webkit-transform: translateY(0px);
                transform: translateY(0px);
            }
        }
        /*END OF SHELF 1*/
        /*PLANT*/
        
        #plant {
            position: relative;
            width: 18px;
            height: 70px;
            margin-top: -70px;
            margin-left: 130px;
        }
        
        #cactus-body,
        #cactus-arm-right,
        #cactus-arm-right-up,
        #cactus-arm-left,
        #cactus-arm-left-up {
            background-color: #84A840;
            border-radius: 25px;
        }
        
        #cactus-body {
            position: relative;
            height: 60px;
            width: 10px;
        }
        
        #cactus-arm-right,
        #cactus-arm-left {
            position: absolute;
            height: 10px;
            width: 25px;
        }
        
        #cactus-arm-right-up,
        #cactus-arm-left-up {
            position: absolute;
            height: 20px;
            width: 10px;
            bottom: 0;
        }
        
        #cactus-arm-left,
        #cactus-arm-right-up {
            right: 0;
        }
        
        #cactus-arm-right,
        #cactus-arm-left-up {
            left: 0;
        }
        
        #cactus-arm-left {
            margin-top: 30px;
        }
        
        #cactus-arm-right {
            margin-top: 18px;
        }
        
        #plant-pot {
            position: relative;
            border-top: 18px solid #8E65A4;
            border-left: 3px solid transparent;
            border-right: 3px solid transparent;
            height: 0;
            width: 20px;
            margin-left: -10px;
            margin-top: -5px;
            cursor: pointer;
        }
        
        #plant-pot:before {
            content: "";
            position: absolute;
            left: -5px;
            top: -28px;
            height: 5px;
            width: 30px;
            border-bottom: 5px solid #4F395C;
        }
        
        #plant:hover #cactus-body {
            -webkit-animation: cactus 0.7s linear infinite;
            animation: cactus 0.7s linear infinite;
            -webkit-transform-origin: bottom;
            -ms-transform-origin: bottom;
            transform-origin: bottom;
            cursor: pointer;
        }
        
        @-webkit-keyframes cactus {
            0% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
            40% {
                -webkit-transform: rotate(-5deg) translate(0px, 2px);
                transform: rotate(-5deg) translate(0px, 2px);
            }
            60% {
                -webkit-transform: rotate(3deg) translate(0px, 2px);
                transform: rotate(3deg) translate(0px, 2px);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        
        @keyframes cactus {
            0% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
            40% {
                -webkit-transform: rotate(-5deg) translate(0px, 2px);
                transform: rotate(-5deg) translate(0px, 2px);
            }
            60% {
                -webkit-transform: rotate(3deg) translate(0px, 2px);
                transform: rotate(3deg) translate(0px, 2px);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        /*END OF PLANT*/
        /*SHELF 2*/
        
        #shelf-area-2 {
            width: auto;
            height: auto;
            display: inline-block;
            margin-top: 90px;
            margin-left: 670px;
            position: absolute;
            z-index: 1;
        }
        
        #shelf-2 {
            position: relative;
            display: inline-block;
            background-color: #F47164;
            width: 200px;
            height: 10px;
        }
        
        #shelf-2-book-1 {
            position: relative;
            background-color: #84A840;
            width: 18px;
            height: 70px;
            margin-top: -70px;
            margin-left: 80px;
        }
        
        #shelf-2-book-1-line-1 {
            position: absolute;
            background-color: #FAE7C7;
            width: 18px;
            height: 3px;
            margin-top: 5px;
        }
        
        #shelf-2-book-1-line-2 {
            position: absolute;
            background-color: #FFF;
            width: 10px;
            height: 25px;
            margin-top: 15px;
            margin-left: 4px;
        }
        
        #shelf-2-book-1-line-3 {
            position: absolute;
            background-color: #FAE7C7;
            width: 8px;
            height: 10px;
            margin-top: 50px;
            margin-left: 5px;
            border-radius: 50%;
        }
        
        #shelf-2-box {
            position: relative;
            background-color: #6686BF;
            width: 45px;
            height: 30px;
            margin-top: -30px;
            margin-left: 135px;
            cursor: pointer;
        }
        
        #shelf-2-box:before {
            content: "";
            position: absolute;
            background-color: #D9EDEE;
            width: 20px;
            height: 8px;
            margin-top: 10px;
            margin-left: 10px;
            border: 1px #3E3F4B solid;
            z-index: 100;
        }
        
        #shelf-2-box:after {
            content: "";
            position: absolute;
            background-color: #3E3F4B;
            width: 49px;
            height: 10px;
            margin-top: -5px;
            margin-left: -2px;
            z-index: 100;
        }
        
        #tape-dispenser {
            position: relative;
            margin-top: -31px;
            margin-left: 40px;
        }
        
        #tape-body {
            position: absolute;
            width: 25px;
            height: 30px;
            background-color: #3F3F4B;
            border-top-left-radius: 15px;
            border-top-right-radius: 15px;
            border-bottom-right-radius: 5px;
        }
        
        #tape-body:before {
            content: "";
            position: absolute;
            width: 28px;
            height: 15px;
            background-color: #3F3F4B;
            bottom: 0;
            margin-left: -25px;
            border-top-left-radius: 5px;
            border-bottom-left-radius: 5px;
        }
        
        #tape-body:after {
            content: "";
            position: absolute;
            background-color: #A5D8DB;
            margin-top: 15px;
            margin-left: -18px;
            height: 5px;
            width: 18px;
            border-radius: 0px 0px 15px 15px;
        }
        
        #tape-legs {
            position: absolute;
            width: 28px;
            height: 2px;
            margin-top: 30px;
            margin-left: -18px;
            border-left: 5px solid #3F3F4B;
            border-right: 5px solid #3F3F4B;
        }
        
        #tape-hole {
            z-index: 100;
            position: absolute;
            background-color: #A5D8DB;
            width: 8px;
            height: 8px;
            margin-top: 8px;
            margin-left: 9px;
            border-radius: 50%;
        }
        
        #tape-roll {
            position: absolute;
            background-color: #FFF;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            margin-top: -5px;
            margin-left: -2.5px;
        }
        
        #tape-roll:after {
            content: "";
            position: absolute;
            background-color: #FFF;
            width: 40px;
            height: 1px;
            -webkit-transform: translate(-25px, 13px) rotate(-10deg);
            -ms-transform: translate(-25px, 13px) rotate(-10deg);
            transform: translate(-25px, 13px) rotate(-10deg);
            -webkit-transform-origin: 100%;
            -ms-transform-origin: 100%;
            transform-origin: 100%;
        }
        
        #shelf-2-book-2 {
            position: relative;
            background-color: #EABBAE;
            width: 10px;
            height: 60px;
            margin-top: -61px;
            margin-left: 115px;
            -webkit-transform: rotate(-15deg);
            -ms-transform: rotate(-15deg);
            transform: rotate(-15deg);
            -webkit-transform-origin: bottom;
            -ms-transform-origin: bottom;
            transform-origin: bottom;
        }
        
        #shelf-2-book-1:hover {
            -webkit-animation: shelf-book-raise 0.8s ease-in forwards;
            animation: shelf-book-raise 0.8s ease-in forwards;
            cursor: pointer;
        }
        
        #shelf-2-book-2:hover {
            -webkit-animation: shelf-book-shift-1 0.8s alternate infinite;
            animation: shelf-book-shift-1 0.8s alternate infinite;
            cursor: pointer;
        }
        
        #shelf-2-box:hover:after {
            -webkit-animation: box-lid 2s ease forwards;
            animation: box-lid 2s ease forwards;
            cursor: pointer;
        }
        
        @-webkit-keyframes box-lid {
            40% {
                -webkit-transform: translate(25px, -18px) rotate(70deg);
                transform: translate(25px, -18px) rotate(70deg);
            }
            60% {
                -webkit-transform: translate(25px, -18px) rotate(70deg);
                transform: translate(25px, -18px) rotate(70deg);
            }
            100% {
                -webkit-transform: translate(0px, 0px) rotate(0deg);
                transform: translate(0px, 0px) rotate(0deg);
            }
        }
        
        @keyframes box-lid {
            40% {
                -webkit-transform: translate(25px, -18px) rotate(70deg);
                transform: translate(25px, -18px) rotate(70deg);
            }
            60% {
                -webkit-transform: translate(25px, -18px) rotate(70deg);
                transform: translate(25px, -18px) rotate(70deg);
            }
            100% {
                -webkit-transform: translate(0px, 0px) rotate(0deg);
                transform: translate(0px, 0px) rotate(0deg);
            }
        }
        
        #box-heart {
            display: inline-block;
            position: absolute;
            width: 12px;
            height: 20px;
            margin-left: -28px;
            z-index: -1;
        }
        
        #box-heart:before,
        #box-heart:after {
            position: absolute;
            content: "";
            left: 50px;
            top: 0;
            width: 12px;
            height: 18px;
            background: #F47164;
            border-radius: 50px 50px 0 0;
            -webkit-transform: rotate(-45deg);
            -ms-transform: rotate(-45deg);
            transform: rotate(-45deg);
            -webkit-transform-origin: 0 100%;
            -ms-transform-origin: 0 100%;
            transform-origin: 0 100%;
            z-index: 100;
        }
        
        #box-heart:after {
            margin-left: 38px;
            left: 0;
            -webkit-transform: rotate(45deg);
            -ms-transform: rotate(45deg);
            transform: rotate(45deg);
            -webkit-transform-origin: 100% 100%;
            -ms-transform-origin: 100% 100%;
            transform-origin: 100% 100%;
        }
        
        #shelf-2-box:hover #box-heart {
            -webkit-animation: pop 2s ease forwards;
            animation: pop 2s ease forwards;
        }
        
        @-webkit-keyframes pop {
            100% {
                -webkit-transform: translateY(-50px) rotate(-20deg);
                transform: translateY(-50px) rotate(-20deg);
                opacity: 0;
            }
        }
        
        @keyframes pop {
            100% {
                -webkit-transform: translateY(-50px) rotate(-20deg);
                transform: translateY(-50px) rotate(-20deg);
                opacity: 0;
            }
        }
        
        #tape-dispenser:hover {
            -webkit-transform-origin: 100%;
            -ms-transform-origin: 100%;
            transform-origin: 100%;
            -webkit-animation: tape 0.5s ease forwards;
            animation: tape 0.5s ease forwards;
            cursor: pointer;
        }
        
        @-webkit-keyframes tape {
            20% {
                -webkit-transform: rotate(5deg);
                transform: rotate(5deg);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        
        @keyframes tape {
            20% {
                -webkit-transform: rotate(5deg);
                transform: rotate(5deg);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        /*END OF SHELF 2*/
        /*PICTURE 1*/
        
        #picture {
            width: auto;
            height: auto;
            display: inline-block;
            margin-top: 20px;
            margin-left: 160px;
            position: absolute;
        }
        
        #picture-1,
        #picture-2 {
            width: 80px;
            height: 100px;
        }
        
        #picture-1,
        #picture-2,
        #picture-3 {
            border: 5px solid #3F3F4B;
            position: relative;
        }
        
        #picture-1,
        #picture-3 {
            margin-left: 110px;
        }
        
        #picture-1 {
            background: url('./hb.gif') center no-repeat;
            background-color: #F7F5F7;
            background-size: 80px 100px;
        }
        
        #picture-2 {
            background: url('./meru.png') center no-repeat;
            background-size: 80px 80px;
            background-color: #D89A8F;
            margin-top: -50px;
        }
        
        #picture-3 {
            background: url('./cupcup.png') center no-repeat;
            background-size: 80px 80px;
            background-color: #B0BBB4;
            width: 100px;
            height: 80px;
            margin-top: -40px;
        }
        
        #picture-1:hover {
            -webkit-animation: picture-1 1s linear forwards;
            animation: picture-1 1s linear forwards;
            -webkit-transform-origin: top;
            -ms-transform-origin: top;
            transform-origin: top;
            cursor: pointer;
        }
        
        @-webkit-keyframes picture-1 {
            20% {
                -webkit-transform: rotate(3deg);
                transform: rotate(3deg);
            }
            50% {
                -webkit-transform: rotate(-3deg);
                transform: rotate(-3deg);
            }
            70% {
                -webkit-transform: rotate(1deg);
                transform: rotate(1deg);
            }
            80% {
                -webkit-transform: rotate(-1deg);
                transform: rotate(-1deg);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        
        @keyframes picture-1 {
            20% {
                -webkit-transform: rotate(3deg);
                transform: rotate(3deg);
            }
            50% {
                -webkit-transform: rotate(-3deg);
                transform: rotate(-3deg);
            }
            70% {
                -webkit-transform: rotate(1deg);
                transform: rotate(1deg);
            }
            80% {
                -webkit-transform: rotate(-1deg);
                transform: rotate(-1deg);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        
        #picture-2:hover {
            -webkit-animation: picture-2 0.5s linear forwards;
            animation: picture-2 0.5s linear forwards;
            cursor: pointer;
        }
        
        @-webkit-keyframes picture-2 {
            50% {
                -webkit-transform: translateY(-5px);
                transform: translateY(-5px);
            }
            100% {
                -webkit-transform: translateY(0px);
                transform: translateY(0px);
            }
        }
        
        @keyframes picture-2 {
            50% {
                -webkit-transform: translateY(-5px);
                transform: translateY(-5px);
            }
            100% {
                -webkit-transform: translateY(0px);
                transform: translateY(0px);
            }
        }
        
        #picture-3:hover {
            -webkit-animation: picture-3 0.5s linear forwards;
            animation: picture-3 0.5s linear forwards;
            -webkit-transform-origin: top left;
            -ms-transform-origin: top left;
            transform-origin: top left;
            cursor: pointer;
        }
        
        @-webkit-keyframes picture-3 {
            50% {
                -webkit-transform: rotate(5deg);
                transform: rotate(5deg);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        
        @keyframes picture-3 {
            50% {
                -webkit-transform: rotate(5deg);
                transform: rotate(5deg);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        /*END OF PICTURE 1*/
        /*POST-ITS*/
        
        #note-1 {
            margin-left: 490px;
            margin-top: 150px;
            -webkit-transform: rotate(8deg);
            -ms-transform: rotate(8deg);
            transform: rotate(8deg);
        }
        
        #note-2 {
            margin-left: 420px;
            margin-top: 170px;
            -webkit-transform: rotate(-10deg);
            -ms-transform: rotate(-10deg);
            transform: rotate(-10deg);
        }
        
        #note-3 {
            margin-left: 480px;
            margin-top: 205px;
            -webkit-transform: rotate(-20deg);
            -ms-transform: rotate(-20deg);
            transform: rotate(-20deg);
        }
        
        #note-4 {
            margin-left: 680px;
            margin-top: 110px;
            -webkit-transform: rotate(-5deg);
            -ms-transform: rotate(-5deg);
            transform: rotate(-5deg);
        }
        
        #note-1,
        #note-2,
        #note-3,
        #note-4 {
            display: inline-block;
            position: absolute;
            background-color: #F4E8C0;
            width: 35px;
            height: 30px;
            left: 0;
            top: 0;
            z-index: 4;
        }
        
        p.note {
            font-size: 9px;
            text-align: center;
            line-height: 10px;
            margin-top: 5px;
        }
        
        #note-4 p {
            font-size: 8px;
            text-align: center;
            line-height: 10px;
            margin-top: 5px;
        }
        
        p.note:hover {
            color: #BD735F;
        }
        /*END OF POST-ITS*/
        /*PHOTOS*/
        
        #photo-1 {
            display: inline-block;
            position: absolute;
            background-color: #F5F0EA;
            width: 50px;
            height: 55px;
            left: 0;
            top: 0;
            z-index: 4;
            margin-left: 580px;
            margin-top: 140px;
            -webkit-transform: rotate(8deg);
            -ms-transform: rotate(8deg);
            transform: rotate(8deg);
            -webkit-transform-origin: top;
            -ms-transform-origin: top;
            transform-origin: top;
        }
        
        #photo-1:before {
            content: "";
            display: inline-block;
            position: absolute;
            width: 40px;
            height: 35px;
            margin-left: 5px;
            margin-top: 5px;
            background: center no-repeat;
            background-size: 40px 30px;
        }
        
        #photo-1:after {
            content: "";
            display: inline-block;
            position: absolute;
            width: 6px;
            height: 6px;
            background-color: #4F395C;
            border-radius: 50%;
            margin-top: -63px;
            margin-left: 22px;
        }
        
        #photo-1:hover {
            -webkit-animation: polaroid-1 1s ease infinite;
            animation: polaroid-1 1s ease infinite;
            -webkit-transform-origin: top;
            -ms-transform-origin: top;
            transform-origin: top;
        }
        
        @-webkit-keyframes polaroid-1 {
            50% {
                -webkit-transform: rotate(3deg);
                transform: rotate(3deg);
            }
        }
        
        @keyframes polaroid-1 {
            50% {
                -webkit-transform: rotate(3deg);
                transform: rotate(3deg);
            }
        }
        
        p.photo,
        p.note {
            font-family: 'Permanent Marker', cursive;
            color: #4F395C;
            text-align: center;
        }
        
        p.photo {
            font-size: 8px;
            margin-top: 40px;
        }
        /*END OF PHOTOS*/
        /*BIG BOX*/
        
        #big-box {
            width: auto;
            height: auto;
            display: inline-block;
            bottom: 0;
            margin-left: 80px;
            position: absolute;
            z-index: 100;
            cursor: pointer;
        }
        
        #big-box-body {
            position: relative;
            background-color: #FFF;
            width: 140px;
            height: 90px;
            z-index: 100;
        }
        
        #big-box-body:after {
            content: "";
            position: absolute;
            background-color: #D9EDEE;
            width: 50px;
            height: 90px;
            right: 0;
            margin-right: -50px;
            z-index: 100;
        }
        
        #big-box-body:before {
            content: "";
            position: absolute;
            background-color: #FAE7C7;
            width: 140px;
            height: 50px;
            top: 0;
            -webkit-transform: skewX(-25deg);
            -ms-transform: skewX(-25deg);
            transform: skewX(-25deg);
            -webkit-transform-origin: top;
            -ms-transform-origin: top;
            transform-origin: top;
            border-radius: 0px 0px 10px 10px;
            z-index: 160;
        }
        
        #big-box-shadow {
            position: absolute;
            z-index: 150;
            border-top: 70px solid #D9EDEE;
            border-left: 0px solid transparent;
            border-right: 20px solid transparent;
            height: 0;
            width: 120px;
            border-bottom-right-radius: 45px;
        }
        
        #big-box-hole {
            position: absolute;
            z-index: 150;
            background-color: #443F4B;
            width: 25px;
            height: 12px;
            margin-left: 155px;
            margin-top: 15px;
            border-radius: 5px;
        }
        
        #box-folder {
            position: absolute;
            background-color: #E4AA9C;
            width: 100px;
            height: 55px;
            z-index: 90;
            margin-top: -110px;
            margin-left: 25px;
            -webkit-transform: rotate(-2deg);
            -ms-transform: rotate(-2deg);
            transform: rotate(-2deg);
            -webkit-transform-origin: bottom left;
            -ms-transform-origin: bottom left;
            transform-origin: bottom left;
        }
        
        #folder-paper,
        #folder-paper-2 {
            width: 60px;
            height: 85px;
            z-index: 50;
            position: absolute;
        }
        
        #folder-paper {
            background-color: #FFF;
            margin-top: -110px;
            margin-left: 70px;
            -webkit-transform: rotate(-85deg);
            -ms-transform: rotate(-85deg);
            transform: rotate(-85deg);
            -webkit-transform-origin: left;
            -ms-transform-origin: left;
            transform-origin: left;
            z-index: 81;
        }
        
        #folder-paper-2 {
            background-color: #D9EDEE;
            margin-top: -80px;
            margin-left: 65px;
            -webkit-transform: rotate(-90deg);
            -ms-transform: rotate(-90deg);
            transform: rotate(-90deg);
            -webkit-transform-origin: left;
            -ms-transform-origin: left;
            transform-origin: left;
            z-index: 80;
        }
        
        #box-folder:before {
            content: "";
            position: absolute;
            width: 40px;
            height: 7px;
            margin-top: -15px;
            left: 0;
            border-bottom: 10px solid #E4AA9C;
            border-left: 0px solid transparent;
            border-right: 5px solid transparent;
        }
        
        p.paper {
            font-size: 8px;
            text-align: left;
            margin-top: 5px;
            margin-left: 5px;
            font-family: 'Permanent Marker', cursive;
            color: #4F395C;
            line-height: 8px;
        }
        
        #big-box:hover #big-box-body:before {
            -webkit-animation: flap 1s ease forwards;
            animation: flap 1s ease forwards;
        }
        
        #big-box:hover #box-folder {
            -webkit-animation: folder 1s ease forwards;
            animation: folder 1s ease forwards;
        }
        
        #big-box:hover #folder-paper {
            -webkit-animation: paper 1s ease forwards;
            animation: paper 1s ease forwards;
        }
        
        #big-box:hover #folder-paper-2 {
            -webkit-animation: paper 1.2s ease forwards;
            animation: paper 1.2s ease forwards;
        }
        
        @-webkit-keyframes flap {
            0% {
                -webkit-transform: rotateX(0deg) skewX(-25deg);
                transform: rotateX(0deg) skewX(-25deg);
            }
            20% {
                -webkit-transform: rotateX(-50deg) skewX(-25deg);
                transform: rotateX(-50deg) skewX(-25deg);
            }
            100% {
                -webkit-transform: rotateX(0deg) skewX(-25deg);
                transform: rotateX(0deg) skewX(-25deg);
            }
        }
        
        @keyframes flap {
            0% {
                -webkit-transform: rotateX(0deg) skewX(-25deg);
                transform: rotateX(0deg) skewX(-25deg);
            }
            20% {
                -webkit-transform: rotateX(-50deg) skewX(-25deg);
                transform: rotateX(-50deg) skewX(-25deg);
            }
            100% {
                -webkit-transform: rotateX(0deg) skewX(-25deg);
                transform: rotateX(0deg) skewX(-25deg);
            }
        }
        
        @-webkit-keyframes folder {
            0% {
                -webkit-transform: translateY(0px) rotate(-2deg);
                transform: translateY(0px) rotate(-2deg);
            }
            100% {
                -webkit-transform: translateY(-10px) rotate(2deg);
                transform: translateY(-10px) rotate(2deg);
            }
        }
        
        @keyframes folder {
            0% {
                -webkit-transform: translateY(0px) rotate(-2deg);
                transform: translateY(0px) rotate(-2deg);
            }
            100% {
                -webkit-transform: translateY(-10px) rotate(2deg);
                transform: translateY(-10px) rotate(2deg);
            }
        }
        
        @-webkit-keyframes paper {
            100% {
                -webkit-transform: translate(5px, -75px) rotate(-35deg);
                transform: translate(5px, -75px) rotate(-35deg);
            }
        }
        
        @keyframes paper {
            100% {
                -webkit-transform: translate(5px, -75px) rotate(-35deg);
                transform: translate(5px, -75px) rotate(-35deg);
            }
        }
        /*END OF BIG BOX*/
        /*WALL OUTLET*/
        
        #outlet {
            width: 25px;
            height: 40px;
            margin-left: 350px;
            margin-top: 600px;
            position: absolute;
            z-index: 1;
            background-color: #FFF;
        }
        
        .outlet-face {
            width: 17px;
            height: 12px;
            margin-left: 4px;
            margin-top: 5px;
            position: relative;
            background-color: #D9EDEE;
            border-radius: 5px;
        }
        
        .outlet-face:before {
            content: "";
            position: absolute;
            margin-top: 3px;
            margin-left: 3px;
            width: 6px;
            height: 5px;
            border-left: #BFDFE4 2px solid;
            border-right: #BFDFE4 2px solid;
        }
        
        #outlet:hover {
            -webkit-animation: outlet 1s linear infinite;
            animation: outlet 1s linear infinite;
            cursor: pointer;
        }
        
        @-webkit-keyframes outlet {
            30% {
                -webkit-transform: rotate(5deg);
                transform: rotate(5deg);
            }
            60% {
                -webkit-transform: rotate(-5deg);
                transform: rotate(-5deg);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        
        @keyframes outlet {
            30% {
                -webkit-transform: rotate(5deg);
                transform: rotate(5deg);
            }
            60% {
                -webkit-transform: rotate(-5deg);
                transform: rotate(-5deg);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        /*END OF WALL OUTLET*/
        /*FLOOR*/
        
        #floor {
            background-color: #BDA382;
            width: 100%;
            height: 18px;
            bottom: 0;
            left: 0;
            z-index: 0;
            position: absolute;
        }
        /*END OF FLOOR*/
        /*FLOOR BINDER*/
        
        #floor-binder {
            width: auto;
            height: auto;
            display: inline-block;
            bottom: 0;
            margin-left: 690px;
            position: absolute;
            z-index: 6;
            cursor: pointer;
        }
        
        #floor-binder-1,
        #floor-binder-2 {
            position: relative;
            background-image: -webkit-gradient(linear, left top, left bottom, color-stop(50%, rgba(165, 216, 219, 1)), color-stop(50%, rgba(255, 255, 255, 1)));
            background-image: -webkit-linear-gradient(rgba(165, 216, 219, 1) 50%, rgba(255, 255, 255, 1) 50%);
            background-image: -o-linear-gradient(rgba(165, 216, 219, 1) 50%, rgba(255, 255, 255, 1) 50%);
            background-image: linear-gradient(rgba(165, 216, 219, 1) 50%, rgba(255, 255, 255, 1) 50%);
            background-size: 1px 2px;
            border-top: 5px solid #3E3F4B;
            border-bottom: 5px solid #3E3F4B;
            border-left: 8px solid #3E3F4B;
            width: 120px;
            height: 22px;
        }
        
        #floor-binder-2 {
            margin-left: 20px;
        }
        
        #floor-binder-1:before,
        #floor-binder-2:before {
            content: "";
            position: absolute;
            background-color: #3E3F4B;
            width: 45px;
            height: 22px;
            margin-left: 45px;
        }
        
        #floor-binder-1:after,
        #floor-binder-2:after {
            content: "";
            position: absolute;
            background-color: #FFF;
            border-radius: 50%;
            width: 8px;
            height: 8px;
            margin-left: 65px;
            margin-top: 10px;
        }
        
        #floor-binder:hover #floor-binder-2 {
            -webkit-animation: bag-binder-2 0.8s linear;
            animation: bag-binder-2 0.8s linear;
        }
        
        #floor-binder:hover #floor-binder-1 {
            -webkit-animation: bag-binder-1 1s linear;
            animation: bag-binder-1 1s linear;
        }
        
        @-webkit-keyframes bag-binder-1 {
            50% {
                -webkit-transform: translateX(-5px);
                transform: translateX(-5px);
            }
            100% {
                -webkit-transform: translateX(0px);
                transform: translateX(0px);
            }
        }
        
        @keyframes bag-binder-1 {
            50% {
                -webkit-transform: translateX(-5px);
                transform: translateX(-5px);
            }
            100% {
                -webkit-transform: translateX(0px);
                transform: translateX(0px);
            }
        }
        
        @-webkit-keyframes bag-binder-2 {
            50% {
                -webkit-transform: translateX(5px);
                transform: translateX(5px);
            }
            100% {
                -webkit-transform: translateX(0px);
                transform: translateX(0px);
            }
        }
        
        @keyframes bag-binder-2 {
            50% {
                -webkit-transform: translateX(5px);
                transform: translateX(5px);
            }
            100% {
                -webkit-transform: translateX(0px);
                transform: translateX(0px);
            }
        }
        /*END OF FLOOR BINDER*/
        /*BAG*/
        
        #bag {
            width: auto;
            height: auto;
            display: inline-block;
            margin-top: 570px;
            margin-left: 710px;
            position: absolute;
            z-index: 6;
            cursor: pointer;
        }
        
        #bag-body,
        #bag-side {
            position: relative;
            height: 80px;
        }
        
        #bag-body {
            background-color: #E4AA9C;
            width: 60px;
            height: 80px;
        }
        
        #bag-side {
            background-color: #C49286;
            width: 20px;
            margin-left: 60px;
        }
        
        #bag-body:after,
        #bag-side:after {
            content: " ";
            display: block;
            position: absolute;
            margin-top: -10px;
            top: 0px;
            left: 0px;
            width: 100%;
            height: 10px;
        }
        
        #bag-body:after {
            background: -webkit-linear-gradient(135deg, #E4AA9C 5px, transparent 0), -webkit-linear-gradient(45deg, #E4AA9C 5px, transparent 0);
            background: -o-linear-gradient(135deg, #E4AA9C 5px, transparent 0), -o-linear-gradient(45deg, #E4AA9C 5px, transparent 0);
            background: linear-gradient(-45deg, #E4AA9C 5px, transparent 0), linear-gradient(45deg, #E4AA9C 5px, transparent 0);
            background-position: left bottom;
            background-repeat: repeat-x;
            background-size: 10px 10px;
        }
        
        #bag-side:after {
            background: -webkit-linear-gradient(135deg, #C49286 5px, transparent 0), -webkit-linear-gradient(45deg, #C49286 5px, transparent 0);
            background: -o-linear-gradient(135deg, #C49286 5px, transparent 0), -o-linear-gradient(45deg, #C49286 5px, transparent 0);
            background: linear-gradient(-45deg, #C49286 5px, transparent 0), linear-gradient(45deg, #C49286 5px, transparent 0);
            background-position: left bottom;
            background-repeat: repeat-x;
            background-size: 10px 10px;
        }
        
        #bag-logo {
            position: absolute;
            background-color: #D9EDEE;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            margin-top: 20px;
            margin-left: 18px;
            z-index: 6;
        }
        
        #bag-logo:before {
            content: "";
            position: absolute;
            border-top: 1px solid #D9EDEE;
            border-bottom: 1px solid #D9EDEE;
            width: 60px;
            height: 5px;
            margin-left: -18px;
            margin-top: 7px;
        }
        
        #bag-handle-front,
        #bag-handle-back {
            border-radius: 40%;
            position: absolute;
            border: #E4AA9C 2px solid;
            height: 50px;
        }
        
        #bag-handle-front {
            width: 30px;
            margin-top: -30px;
            margin-left: 15px;
        }
        
        #bag-handle-back {
            width: 28px;
            margin-top: -28px;
            margin-left: 28px;
        }
        
        #bag.animated {
            -webkit-animation: bag 1s linear;
            animation: bag 1s linear;
        }
        
        @-webkit-keyframes bag {
            20% {
                -webkit-transform: translateY(-20px) rotate(10deg);
                transform: translateY(-20px) rotate(10deg);
            }
            40% {
                -webkit-transform: translateY(-25px) rotate(0deg);
                transform: translateY(-25px) rotate(0deg);
            }
            60% {
                -webkit-transform: translateY(-20px) rotate(-5deg);
                transform: translateY(-20px) rotate(-5deg);
            }
        }
        
        @keyframes bag {
            20% {
                -webkit-transform: translateY(-20px) rotate(10deg);
                transform: translateY(-20px) rotate(10deg);
            }
            40% {
                -webkit-transform: translateY(-25px) rotate(0deg);
                transform: translateY(-25px) rotate(0deg);
            }
            60% {
                -webkit-transform: translateY(-20px) rotate(-5deg);
                transform: translateY(-20px) rotate(-5deg);
            }
        }
        
        p.bag {
            position: absolute;
            display: inline-block;
            font-family: "Pacifico", cursive;
            font-size: 14px;
            color: #D9EDEE;
            margin-left: 2px;
            margin-top: 40px;
            -webkit-transform: rotate(-10deg);
            -ms-transform: rotate(-10deg);
            transform: rotate(-10deg);
        }
        /*END OF BAG*/
        
        #ipucu {
            font-size: 16px;
            display: inline-block;
            width: 200px;
            height: 100px;
            border: 5px solid #3F3F4B;
            background-color: #EABBAE;
        }
        
        #ipucu:hover {
            -webkit-animation: ipucu 1s linear forwards;
            animation: ipucu 1s linear forwards;
            -webkit-transform-origin: top;
            -ms-transform-origin: top;
            transform-origin: top;
            cursor: pointer;
        }
        
        p.note2 {
            font-family: 'Permanent Marker', cursive;
            font-size: 16px;
            text-align: center;
            line-height: 25px;
            margin-top: 5px;
        }
        
        p.note2:hover {
            color: #BD735F;
        }
        
        @-webkit-keyframes ipucu {
            20% {
                -webkit-transform: rotate(3deg);
                transform: rotate(3deg);
            }
            50% {
                -webkit-transform: rotate(-3deg);
                transform: rotate(-3deg);
            }
            70% {
                -webkit-transform: rotate(1deg);
                transform: rotate(1deg);
            }
            80% {
                -webkit-transform: rotate(-1deg);
                transform: rotate(-1deg);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        
        @keyframes ipucu {
            20% {
                -webkit-transform: rotate(3deg);
                transform: rotate(3deg);
            }
            50% {
                -webkit-transform: rotate(-3deg);
                transform: rotate(-3deg);
            }
            70% {
                -webkit-transform: rotate(1deg);
                transform: rotate(1deg);
            }
            80% {
                -webkit-transform: rotate(-1deg);
                transform: rotate(-1deg);
            }
            100% {
                -webkit-transform: rotate(0deg);
                transform: rotate(0deg);
            }
        }
        /* modal */
        
        .modal,
        .modal-box {
            z-index: 900;
        }
        
        .modal-sandbox {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            background: transparent;
        }
        
        .modal {
            display: none;
            position: fixed;
            width: 100%;
            height: 100%;
            left: 0;
            top: 0;
            background: rgb(0, 0, 0);
            background: rgba(0, 0, 0, .8);
            overflow: auto;
        }
        
        .modal-box {
            position: relative;
            width: 80%;
            max-width: 500px;
            margin: 100px auto;
            animation-name: modalbox;
            animation-duration: .4s;
            animation-timing-function: cubic-bezier(0, 0, .3, 1.6);
        }
        
        .modal-header {
            padding: 10px 20px;
            background: #546E7A;
            color: #ffffff;
        }
        /* Close Button */
        
        .close-modal {
            text-align: right;
            cursor: pointer;
        }
        /* Animation */
        
        @-webkit-keyframes modalbox {
            0% {
                top: -250px;
                opacity: 0;
            }
            100% {
                top: 0;
                opacity: 1;
            }
        }
        
        @keyframes modalbox {
            0% {
                top: -250px;
                opacity: 0;
            }
            100% {
                top: 0;
                opacity: 1;
            }
        }
        /* Aditional Styles */
        
        .modal-trigger {
            position: absolute;
            top: 50%;
            left: 50%;
            -webkit-transform: translate(-50%, -50%);
            -ms-transform: translate(-50%, -50%);
            -o-transform: translate(-50%, -50%);
            transform: translate(-50%, -50%);
            transition: ease .2s;
        }
        
        .modal-trigger:hover {
            padding: 20px 60px;
        }
        /* questions css */
        
        .container ul {
            list-style: none;
            margin: 0;
            padding: 0;
            overflow: auto;
        }
        
        ul li {
            color: #AAAAAA;
            display: block;
            position: relative;
            float: left;
            width: 100%;
            height: 100px;
            border-bottom: 1px solid #333;
        }
        
        ul li input[type=radio] {
            position: absolute;
            visibility: hidden;
        }
        
        ul li label {
            display: block;
            position: relative;
            font-weight: 300;
            font-size: 1.35em;
            padding: 25px 25px 25px 80px;
            margin: 10px auto;
            height: 30px;
            z-index: 9;
            cursor: pointer;
        }
        
        ul li:hover label {
            color: #FFFFFF;
        }
        
        ul li .check {
            display: block;
            position: absolute;
            border: 5px solid #AAAAAA;
            border-radius: 100%;
            height: 25px;
            width: 25px;
            top: 30px;
            left: 20px;
            z-index: 5;
            transition: border .25s linear;
            -webkit-transition: border .25s linear;
        }
        
        ul li:hover .check {
            border: 5px solid #FFFFFF;
        }
        
        ul li .check::before {
            display: block;
            position: absolute;
            content: '';
            border-radius: 100%;
            height: 15px;
            width: 15px;
            top: 5px;
            left: 5px;
            margin: auto;
            transition: background 0.25s linear;
            -webkit-transition: background 0.25s linear;
        }
        
        input[type=radio]:checked~.check {
            border: 5px solid #0DFF92;
        }
        
        input[type=radio]:checked~.check::before {
            background: #0DFF92;
        }
        
        input[type=radio]:checked~label {
            color: #0DFF92;
        }
        
        .right {
            background: #0DFF92;
            color: #0a0a0a;
        }
        
        .wrong {
            background: #F47164;
            color: #0a0a0a;
        }
    </style>

</head>

<body>

    <div id="ipucu">
        <p class="note2">ipucu: ofisten kaçmak için soruları bulup çözmelisin....</p>
    </div>
    <div class="modal" id="modal-name" style="display: none;">
        <div class="modal-sandbox"></div>
        <div class="modal-box">
            <div class="modal-header">
                <div class="close-modal">&#10006;</div>
                <div id="questions">
                    <div class="container">
                        <h3 id='soru'></h3>
                        <ul>
                            <li>
                                <input type="radio" id="f-option" name="selector" class="success">
                                <label for="f-option" id='cvp1'></label>
                                <div class="check"></div>
                            </li>

                            <li>
                                <input type="radio" id="s-option" name="selector" class="success">
                                <label for="s-option" id='cvp2'></label>
                                <div class="check">
                                    <div class="inside"></div>
                                </div>
                            </li>

                            <li>
                                <input type="radio" id="t-option" name="selector" class="success">
                                <label for="t-option" id='cvp3'></label>
                                <div class="check">
                                    <div class="inside"></div>
                                </div>
                            </li>

                            <li>
                                <input type="radio" id="y-option" name="selector" class="success">
                                <label for="y-option" id='cvp4'></label>
                                <div class="check">
                                    <div class="inside"></div>
                                </div>
                            </li>
                        </ul>
                    </div>
                    <div class="rightAnswer" style="display: none;">
                        <span class="right">DOĞRU!!</span>
                    </div>
                    <div class="wrongAnswer" style="display: none;">
                        <span class="wrong">YANLIŞ!! BİR DAHA DENE :(</span>
                    </div>
                    <div class="video" style="display: none;">
                        <span class="right">Bütün Soruları Doğru Yanıtladın ve Ofisten Kaçmayı Başardın.. Happy Birthday!!</span>
                        <video width="320" height="240" controls>
                        <source src="1623584764105.mp4" type="video/mp4">
                      </video>
                    </div>

                </div>
            </div>
        </div>
    </div>

    <!--FLOOR-->
    <div id="floor"></div>
    <!--END OF FLOOR-->

    <div id="scene">

        <!--CLOCK-->
        <div id="clock">
            <div id="clock-face">
                <div class="clock-marker" id="clock-marker-12-6"></div>
                <div class="clock-marker" id="clock-marker-1-7"></div>
                <div class="clock-marker" id="clock-marker-2-8"></div>
                <div class="clock-marker" id="clock-marker-3-9"></div>
                <div class="clock-marker" id="clock-marker-4-10"></div>
                <div class="clock-marker" id="clock-marker-5-11"></div>
                <div id="clock-inner"></div>
                <div class="hand hour"></div>
                <div class="hand minute"></div>
                <div class="hand second"></div>
                <div id="clock-dot"></div>
            </div>
        </div>
        <!--END OF CLOCK-->

        <!--BOOK STACK-->
        <div id="stack-book">
            <div id="stack-book-1"></div>
            <div class="stack-book-2"></div>
            <div class="stack-book-3"></div>
            <div class="stack-book-4"></div>
            <div id="stack-book-5"></div>
            <div class="stack-book-6"></div>
            <div class="stack-book-7"></div>
            <div id="stack-book-8"></div>
            <div class="stack-book-9"></div>
            <div id="stack-book-10"></div>
            <div id="stack-book-11"></div>
            <div id="stack-book-12"></div>
        </div>
        <!--END OF BOOK STACK-->

        <!--BINDER STACK-->
        <div id="stack-binder">
            <div id="stack-binder-1">
                <div class="stack-binder-right-bind" id="stack-binder-1-bind">
                    <div class="stack-binder-right-top stack-binder-1-tb"></div>
                    <div class="stack-binder-right-ring">
                        <div class="stack-binder-right-paper"></div>
                    </div>
                    <div class="stack-binder-right-bottom stack-binder-1-tb"></div>
                </div>
            </div>
            <div id="stack-binder-2">
                <div class="stack-binder-left-bind stack-binder-4-bind">
                    <div class="stack-binder-left-top stack-binder-4-tb"></div>
                    <div class="stack-binder-left-ring">
                        <div class="stack-binder-left-paper"></div>
                    </div>
                    <div class="stack-binder-left-bottom stack-binder-4-tb"></div>
                </div>
            </div>
            <div id="stack-binder-3">
                <div class="stack-binder-right-bind" id="stack-binder-3-bind">
                    <div class="stack-binder-right-top stack-binder-3-tb"></div>
                    <div class="stack-binder-right-ring">
                        <div class="stack-binder-right-paper"></div>
                    </div>
                    <div class="stack-binder-right-bottom stack-binder-3-tb"></div>
                </div>
            </div>
            <div id="stack-binder-4">
                <div class="stack-binder-left-bind stack-binder-4-bind">
                    <div class="stack-binder-left-top stack-binder-4-tb"></div>
                    <div class="stack-binder-left-ring">
                        <div class="stack-binder-left-paper"></div>
                    </div>
                    <div class="stack-binder-left-bottom stack-binder-4-tb"></div>
                </div>
            </div>
            <!-- <audio class="sound" preload="auto">
        <source src="http://jackiezen.com/Office/sounds/binder.mp3" />
      </audio> -->
        </div>
        <!--END OF BINDER STACK-->

        <!--PENCIL HOLDER CONTENTS-->
        <div id="pencil-holder-contents">
            <div id="pencil-cup">
                <div id="heart"></div>
            </div>
            <div id="pencil-holder">
                <div id="ruler">
                    <div id="ruler-inner"></div>
                </div>
                <div id="pencil-1">
                    <div class="pencil-tip">
                        <div class="pencil-tip-top"></div>
                    </div>
                </div>
                <div id="pencil-2">
                    <div class="pencil-tip">
                        <div class="pencil-tip-top"></div>
                    </div>
                </div>
            </div>
        </div>
        <!--END OF PENCIL HOLDER CONTENTS-->

        <!--COFFEE CUP-->
        <div id="coffee-cup">
            <div id="coffee-cup-top">
                <div id="coffee-cup-rim"></div>
            </div>
            <div id="coffee-cup-bottom">

                <div id="coffee-cup-holder">
                    <div id="coffee-cup-logo"></div>
                </div>
                <p class="cup">Deniz Damla Deniz</p>
            </div>
            <!-- <audio class="sound" preload="auto" loop>
        <source src="http://jackiezen.com/Office/sounds/coffee.mp3" />
      </audio> -->
        </div>
        <!--END OF COFFEE CUP-->

        <!--BOOK STACK-->
        <div id="stack-book-small">
            <div class="stack-book-2"></div>
            <div class="stack-book-4"></div>
            <div class="stack-book-3"></div>
            <div class="stack-book-7"></div>
            <div class="stack-book-6"></div>
            <div class="stack-book-9"></div>
        </div>
        <!--END OF BOOK STACK-->

        <!--TAKE-OUT-->
        <div id="take-out">
            <div id="take-out-box">
                <div id="take-out-box-top"></div>
                <div id="take-out-box-bottom">
                    <div id="take-out-box-handle">
                        <div id="take-out-box-handle-dot"></div>
                    </div>
                </div>
                <div id="take-out-box-bottom-back">
                    <p class="box">Zula
                        <br>Burger</p>
                </div>
            </div>
            <div id="chopsticks">
                <div id="chopsticks-1"></div>
                <div id="chopsticks-2"></div>
            </div>
            <!-- <audio class="sound" preload="auto">
        <source src="http://jackiezen.com/Office/sounds/chopsticks.mp3" />
      </audio> -->
        </div>
        <!--END OF TAKE-OUT-->

        <!--COMPUTER-->
        <div id="computer">
            <div id="computer-side">
                <div id="computer-back">
                    <div id="computer-logo"></div>
                    <div id="computer-logo-bite"></div>
                    <div id="computer-logo-stem"></div>
                    <div id="computer-logo-leaf"></div>
                </div>
            </div>
            <div id="computer-stand">
                <div id="computer-stand-shadow"></div>
                <div id="computer-stand-hole"></div>
                <div id="computer-cable"></div>
            </div>
            <div id="computer-stand-bottom"></div>
            <div id="computer-stand-curve"></div>
        </div>
        <!--END OF COMPUTER-->

        <!--CHAIR-->
        <div id="chair">
            <div id="chair-seat">
                <div id="chair-arm-left"></div>
                <div id="chair-back"></div>
                <div id="chair-spine"></div>
                <div id="chair-pole">
                    <div id="chair-rod"></div>
                </div>
                <div id="chair-arm-right"></div>
                <div id="chair-legs">
                    <div id="chair-leg-left">
                        <div id="left-wheel"></div>
                    </div>
                    <div id="chair-leg-middle">
                        <div id="middle-wheel"></div>
                    </div>
                    <div id="chair-leg-right">
                        <div id="right-wheel"></div>
                    </div>
                </div>
            </div>
            <!-- <audio class="sound" preload="auto">
        <source src="http://jackiezen.com/Office/sounds/chair.mp3" />
      </audio> -->
        </div>
        <!--END OF CHAIR-->

        <!--SHELF 1-->
        <div id="shelf-area">
            <div id="shelf-1">
                <div id="shelf-1-book-1">
                    <div id="shelf-1-book-1-line-1"></div>
                    <div id="shelf-1-book-1-line-2"></div>
                    <div id="shelf-1-book-1-line-3"></div>
                </div>
                <div id="shelf-1-book-2">
                    <div id="shelf-1-book-2-line-1"></div>
                    <div id="shelf-1-book-2-line-2"></div>
                    <div id="shelf-1-book-2-line-3"></div>
                </div>
                <div id="shelf-1-book-3"></div>
                <div id="shelf-1-book-4"></div>
                <div id="plant">
                    <div id="cactus-body">
                        <div id="cactus-arm-left">
                            <div id="cactus-arm-left-up"></div>
                        </div>
                        <div id="cactus-arm-right">
                            <div id="cactus-arm-right-up"></div>
                        </div>
                    </div>
                    <div id="plant-pot"></div>
                    <!-- <audio class="sound" preload="auto">
            <source src="http://jackiezen.com/Office/sounds/cactus.mp3" />
          </audio> -->
                </div>
            </div>
        </div>
        <!--END OF SHELF 2-->

        <!--SHELF 2-->
        <div id="shelf-area-2">
            <div id="shelf-2">
                <div id="shelf-2-box">
                    <div id="box-heart"></div>
                    <!-- <audio class="sound" preload="auto">
            <source src="http://jackiezen.com/Office/sounds/box.mp3" />
          </audio> -->
                </div>
                <div id="shelf-2-book-1">
                    <div id="shelf-2-book-1-line-1"></div>
                    <div id="shelf-2-book-1-line-2"></div>
                    <div id="shelf-2-book-1-line-3"></div>
                </div>
                <div id="shelf-2-book-2"></div>
                <div id="tape-dispenser">
                    <div id="tape-roll"></div>
                    <div id="tape-body">
                        <div id="tape-legs"></div>
                        <div id="tape-hole"></div>
                    </div>
                    <!-- <audio class="sound" preload="auto">
            <source src="http://jackiezen.com/Office/sounds/tape.mp3" />
          </audio> -->
                </div>
            </div>
        </div>
        <!--END OF SHELF 2-->

        <!--PICTURES-->
        <div id="picture">
            <div id="picture-1"></div>
            <div id="picture-2"></div>
            <div id="picture-3"></div>
        </div>
        <!--END OF PICTURES-->

        <!--POST-ITS-->
        <div class="drag" id="note-1" draggable="true">
            <p class="note">Love You!</p>
        </div>
        <div class="drag" id="note-2" draggable="true">
            <p class="note">Özge'yi Ara</p>
        </div>
        <div class="drag" id="note-3" draggable="true">
            <p class="note">Kedileri Besle</p>
        </div>
        <div class="drag" id="note-4" draggable="true">
            <p class="note">Çiçeği Sula</p>
        </div>
        <!--END OF POST-ITS-->

        <!--PHOTOS-->
        <div class="drag" id="photo-1">
            <p class="photo">well</p>
        </div>
        <!--END OF PHOTOS-->

        <!--DESK-->
        <div id="desk">
            <div id="desk-top-1"></div>
            <div id="desk-top-2"></div>
            <div id="desk-top-3">
                <div id="desk-top-3-left"></div>
                <div id="desk-top-3-right"></div>
            </div>
            <div id="desk-leg-left"></div>
            <div id="desk-leg-right"></div>
        </div>
        <!--END OF DESK-->

        <!--BIG BOX-->
        <div id="big-box">
            <div id="big-box-body">
                <div id="big-box-shadow"></div>
                <div id="big-box-hole"></div>
            </div>
            <div id="box-folder"></div>
            <div id="folder-paper">
                <p class="paper">My Love,
                    <br>
                    <br>Don't Forget that I love You So Much!
                    <br>
                    <br>
                    <br>Love,
                    <br>Özge</p>
            </div>
            <div id="folder-paper-2">
                <p class="paper">Grocery List
                    <br>
                    <br>Socks
                    <br>Shoes
                    <br>Shorts
                    <br>Coffee
                    <br>Cigarettes</p>
            </div>
            <!-- <audio class="sound" preload="auto">
        <source src="http://jackiezen.com/Office/sounds/paper.mp3" />
      </audio> -->
        </div>
        <!--END OF BIG BOX-->

        <!--WALL OUTLET-->
        <div id="outlet">
            <div id="first" class="modal-trigger">
                <div class="outlet-face "></div>
                <div class="outlet-face"></div>
            </div>
        </div>
        <!--END OF WALL OUTLET-->

        <!--BAG-->
        <div id="bag">
            <div id="bag-body">
                <div id="bag-logo"></div>
                <p class="bag">Reebok</p>
                <div id="bag-handle-front"></div>
                <div id="bag-handle-back"></div>
                <div id="bag-side"></div>
            </div>
            <!-- <audio class="sound" preload="auto">
        <source src="http://jackiezen.com/Office/sounds/bag.mp3" />
      </audio> -->
        </div>
        <!--END OF BAG-->

        <!--FLOOR BINDER-->
        <div id="floor-binder">
            <div id="floor-binder-1"></div>
            <div id="floor-binder-2"></div>
        </div>
        <!--END OF FLOOR BINDER-->

    </div>
</body>
<script>
    $(document).ready(function() {

        //-----------------------------------------------------------------
        // jquery for animations from original source
        //-----------------------------------------------------------------

        $(".drag").draggable().css('cursor', 'pointer');
        $("#chair-seat, #bag, #chair").bind("webkitAnimationEnd mozAnimationEnd animationEnd", function() {
            $(this).removeClass("animated");

        });

        $("#chair-seat, #bag, #chair").hover(function() {
            $(this).addClass("animated");
        });

        //-----------------------------------------------------------------
        //-----------------------------------------------------------------
        //-----------------------------------------------------------------



        //-----------------------------------------------------------------
        // close to the modal 
        //-----------------------------------------------------------------
        let modal = document.getElementById('modal-name');
        let closeModalClass = document.getElementsByClassName('close-modal')[0];
        let modalSendBox = document.getElementsByClassName('modal-sandbox')[0];

        modalSendBox.addEventListener("click", () => {
            closeModal();
        });

        closeModalClass.addEventListener("click", () => {
            closeModal();
        });

        function closeModal() {
            modal.style.display = "none";

        }
        //-----------------------------------------------------------------
        //-----------------------------------------------------------------
        //-----------------------------------------------------------------


        //-----------------------------------------------------------------
        // Preparing the questions
        //-----------------------------------------------------------------

        let birinciSoru = document.getElementById('outlet');
        let ikinciSoru = document.getElementById('shelf-1-book-1-line-2');
        let ucuncuSoru = document.getElementById('big-box-body');
        let dorduncuSoru = document.getElementById('coffee-cup-holder');
        let besinciSoru = document.getElementById('ruler');
        let altinciSoru = document.getElementById('tape-hole');

        let container = document.querySelector('.container');
        let rightAnswer = document.querySelector('.rightAnswer');
        let wrongAnswer = document.querySelector('.wrongAnswer');

        let soruLabel = document.querySelector('#soru');
        let cvp1Label = document.querySelector('#cvp1');
        let cvp2Label = document.querySelector('#cvp2');
        let cvp3Label = document.querySelector('#cvp3');
        let cvp4Label = document.querySelector('#cvp4');

        let radio1 = document.getElementById('f-option');
        let radio2 = document.getElementById('s-option');
        let radio3 = document.getElementById('t-option');
        let radio4 = document.getElementById('y-option');

        let video = document.querySelector('.video');


        let answers = [];



        let q1 = {
            soru: "Hangisini FlorMLARM dan aldım?",
            cvp1: "Çık arkamdan ÇIAAAĞKKKK",
            cvp2: "Tasarımımı yapabilir miyim ??!! TAMAM! Mekaup!!!!",
            cvp3: "Yani bunu çok severim, çok seeveerimm tililililillililili Tavsiyem Size Tavsiyemdir Yani",
            cvp4: "Yüzümü şekilleştiriyii ya çok güsel oluyi yanii"
        }

        let q2 = {
            soru: "Bakalım Pundixlerim 2 Katına Çıkmış mı?",
            cvp1: "Yarıya Düşmüş",
            cvp2: "PUNDIX in allah belasını versin",
            cvp3: "10x yapmış",
            cvp4: "PUNDIX ne ki bir yemek türü mü?"
        }

        let q3 = {
            soru: "Sefer Amca Sen Ne Yaptın?",
            cvp1: "Beni öldürecekti kendi gitti",
            cvp2: "Kader Olaraktan",
            cvp3: "Kendini Ben Öldürmüş Oldum",
            cvp4: "Olmasa iyiydi işte ama oldu napalım"
        }

        let q4 = {
            soru: "Hangisi çocuğunun doğumundan sonra disipline girmiştir?",
            cvp1: "Yediği kaba pisleyen Şerefsiz Erol Köse",
            cvp2: "Tuvaleti dışarda olan gecekondu çocukları",
            cvp3: "Köpek gibi çalışıp kraliçeler gibi yaşamaya çalışan Seda Sayan",
            cvp4: "Ekrandan memeleri ağzımıza giren Erol Köse'nin Karısı olan kadın."
        }

        let q5 = {
            soru: "Neden Deppoya Ateş Ettiniz?",
            cvp1: "Ağzımız da niyetliydi bizim",
            cvp2: "Zaten tedbirli olsak o insanlar içeriye giremezdikine,nasıl girecen 1 tane kapı var!?",
            cvp3: "Kendinlerini süpermen mi sanıyor onlar?",
            cvp4: "Masum insanlara vurmak bize yakışmaz."
        }


        let q6 = {
            soru: "Hangi Kanalın Etrafını Çerçeve Yapmamışlar?",
            cvp1: "Lanet olası kanalın",
            cvp2: "düştüm çıkaramıyorum, pisikleti düldülü çıkaramıyorum",
            cvp3: "Bizim buraya bissürü çocuğumuz var",
            cvp4: "Amma ahşam amma ğündüz"
        }

        let questions = [q1, q2, q3, q4, q5, q6];

        birinciSoru.addEventListener("click", () => {
            showQuestions(0);
        });

        ikinciSoru.addEventListener("click", () => {
            showQuestions(1);
        });

        ucuncuSoru.addEventListener("click", () => {
            showQuestions(2);
        });

        dorduncuSoru.addEventListener("click", () => {
            showQuestions(3);
        });

        besinciSoru.addEventListener("click", () => {
            showQuestions(4);
        });

        altinciSoru.addEventListener("click", () => {
            showQuestions(5);
        });


        function showQuestions(num) {
            container.style.display = "block";
            modal.style.display = "block";
            rightAnswer.style.display = "none";
            wrongAnswer.style.display = "none";
            video.style.display = 'none';

            radio1.checked = false;
            radio2.checked = false;
            radio3.checked = false;
            radio4.checked = false;

            soruLabel.textContent = questions[num].soru;
            cvp1Label.textContent = questions[num].cvp1;
            cvp2Label.textContent = questions[num].cvp2;
            cvp3Label.textContent = questions[num].cvp3;
            cvp4Label.textContent = questions[num].cvp4;


            radio1.addEventListener("click", () => {
                showAnswer(num, 1);
            });
            radio2.addEventListener("click", () => {
                showAnswer(num, 2);
            });
            radio3.addEventListener("click", () => {
                showAnswer(num, 3);
            });
            radio4.addEventListener("click", () => {
                showAnswer(num, 4);
            });

            function showAnswer(index, radio) {

                if (index == 0 && radio == 4) {
                    showDogruCevap(index);
                    $(birinciSoru).replaceWith($(birinciSoru).clone());
                } else if (index == 1 && radio == 1) {
                    showDogruCevap(index);
                    $(ikinciSoru).replaceWith($(ikinciSoru).clone());
                } else if (index == 2 && radio == 3) {
                    showDogruCevap(index);
                    $(ucuncuSoru).replaceWith($(ucuncuSoru).clone());
                } else if (index == 3 && radio == 3) {
                    showDogruCevap(index);
                    $(dorduncuSoru).replaceWith($(dorduncuSoru).clone());
                } else if (index == 4 && radio == 3) {
                    showDogruCevap(index);
                    $(besinciSoru).replaceWith($(besinciSoru).clone());
                } else if (index == 5 && radio == 1) {
                    showDogruCevap(index);
                    $(altinciSoru).replaceWith($(altinciSoru).clone());
                } else {
                    showYanlisCevap();
                }
            }

        }




        // show right answer 
        function showDogruCevap(index) {
            container.style.display = "none";
            wrongAnswer.style.display = "none";
            rightAnswer.style.display = "inline";
            answers.push(index);
            setTimeout(console.log(''), 1500);
            setTimeout(closeModal, 1500);
            setTimeout(checkifEnded, 2000);

        }

        function showYanlisCevap() {
            container.style.display = "none";
            rightAnswer.style.display = "none";
            wrongAnswer.style.display = "inline";
            setTimeout(console.log(''), 1500);
            setTimeout(closeModal, 1500);
        }


        function onlyUnique(value, index, self) {
            return self.indexOf(value) === index;
        }


        function checkifEnded() {
            var unique = answers.filter(onlyUnique);
            unique.sort(function(a, b) {
                return a - b;
            });
            if (unique.length == 6) { // tum sorular cevaplandi
                container.style.display = "none";
                modal.style.display = "block";
                rightAnswer.style.display = "none";
                wrongAnswer.style.display = "none";
                video.style.display = 'block';
            }
        }

        //-----------------------------------------------------------------
        //-----------------------------------------------------------------
        //-----------------------------------------------------------------


    });
</script>

</html>
