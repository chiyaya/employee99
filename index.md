<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, user-scalable=no">
  <link href="http://jqmdesigner.appspot.com/gk/lib/jquery.mobile/1.4.5/jquery.mobile-1.4.5.min.css" rel="stylesheet" type="text/css" />
  <!-- Export CSS  -->
  <style>
    @import url(http://fonts.googleapis.com/css?family=Titillium+Web);
     @media screen and (max-width: 400px) {
      .gk-component-simple-weather h2 {
        margin-top: -5px!important;
        font-size: 50px!important;
      }
      .gk-component-simple-weather i {
        width: 120px!important;
        height: 90px!important;
      }
      .gk-component-simple-weather i img {
        width: 180px!important;
      }
    }
    .gk-component-simple-weather {
      width: 80%;
      margin: 0 auto;
      text-align: center;
      text-transform: uppercase;
      border: 1px solid #999;
      -webkit-border-radius: 15px;
      -moz-border-radius: 15px;
      border-radius: 15px;
      background: -webkit-linear-gradient(top, #999 0%, #ccc 30%, #aaa 70%, #888 100%);
      background: -moz-linear-gradient(top, #999 0%, #ccc 30%, #aaa 70%, #888 100%);
      background: linear-gradient(top, #999 0%, #ccc 30%, #aaa 70%, #888 100%);
      box-shadow: 0 4px 10px rgba(0, 0, 0, .9)
    }
    .gk-component-simple-weather i {
      display: block;
      width: 140px;
      height: 100px;
      margin: 10px auto 0;
      overflow: hidden;
    }
    .gk-component-simple-weather i img {
      width: 200px;
    }
    .gk-component-simple-weather h2 {
      margin: 0 0 8px;
      color: #fff;
      font-size: 70px;
      font-weight: 300;
      text-align: center;
      text-shadow: 0px 1px 3px rgba(0, 0, 0, 0.25);
    }
    .gk-component-simple-weather ul {
      margin: 0 10px 10px;
      padding: 0;
    }
    .gk-component-simple-weather li {
      font-family: "Titillium Web";
      background: #fff;
      background: rgba(255, 255, 255, 0.6);
      padding: 4px 8px;
      display: inline-block;
      border-radius: 5px;
      box-shadow: inset 0 1px 1px rgba(0, 0, 0, .7);
      margin: 0 2px 10px;
      font-size: 12px;
    }
    .gk-component-simple-weather p {
      font-family: "Titillium Web";
      text-shadow: none;
      font-size: 12px;
    }
  </style>
  <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
  <script>
    $(document).on("mobileinit", function () {
      $.mobile.autoInitializePage = false;
      $.mobile.hashListeningEnabled = false;
    });

    function mobileInitPage() {
      $.mobile.hashListeningEnabled = true;
      $.mobile.initializePage();
    };
  </script>
  <script src="http://code.jquery.com/mobile/1.4.5/jquery.mobile-1.4.5.min.js"></script>
  <!-- Uncomment the following to include cordova in your android project -->
  <!--<script src="http://jqmdesigner.appspot.com/platforms/android/cordova.js"></script>-->
  <!-- GK Loader use RequireJS to load module -->
  <script src="http://requirejs.org/docs/release/2.1.11/minified/require.js"></script>
  <!--Plug in GK-->
  <script src="http://jqmdesigner.appspot.com/components/jquery.gk/jquery.gk.min.js"></script>
  <!-- Load GK components -->
  <script components="http://jqmdesigner.appspot.com/components/gk-ext/image.html,http://jqmdesigner.appspot.com/components/gk-jquerymobile/content.html,http://jqmdesigner.appspot.com/components/gk-jquerymobile/page.html,http://jqmdesigner.appspot.com/components/gk-jquerymobile/button.html,http://jqmdesigner.appspot.com/components/gk-jquerymobile/footer.html,http://jqmdesigner.appspot.com/components/gk-jquerymobile/listview-li.html,http://jqmdesigner.appspot.com/components/gk-jquerymobile/header.html,http://jqmdesigner.appspot.com/components/gk-ext/json-listview.html"
  callback="mobileInitPage" src="http://jqmdesigner.appspot.com/components/gk-loader/gk-loader.js"></script>
  <!-- Export JS  -->
  <script>
    $(document).on("pageinit", "#home", function () {
      var $ele = $("#gk-12KIDw"),
        url = $ele.attr("service");
      if (url) {
        $.getJSON(url).complete(function (data) {
          $("#gk-12KIDw").gk("model", $.parseJSON(data.responseText));

          $('#gk-12KIDw a').on('click', function (e) {
            var g1 = $(this).attr('s1');
            var g2 = $(this).attr('s2');
            var g3 = $(this).attr('s3');
            var g4 = $(this).attr('s4');
            var g5 = $(this).attr('s5');
            var g6 = $(this).attr('s6');
            $('.d1').text(g1);
            $('.d2').text(g2);
            $('.d3').text(g3);
            $('.d4').text(g4);
            $('.d5').text(g5);
            $('.d6').text(g6);
            //$('#map1').gk('address', g2);
            $('#img').attr('src', g6);
          });



        });
      }
    });
  </script>
  <title>EZo App</title>
</head>

<body gk-app>
  <!-- Page: home  -->
  <div is="page" id="home" data-role="page">
    <div is="header" data-role="header" data-position="fixed" data-theme="b">
      <h3>Allen集團人事資料</h3>
    </div>
    <div is="content" role="main" class="ui-content">
      <ul id="gk-12KIDw" data-filter="true" data-role="listview" data-autodividers="true" data-inset="true" is="json-listview" service="https://chiyaya.github.io/joson/employee.json" data-divider-theme="b">
        <li divider="{{department}}" is="listview-li">
          <a href="#detail" s1="{{firstName}}" s2="{{lastName}}" s3="{{title}}" s4="{{cellPhone}}" s5="{{email}}" s6="https://chiyaya.github.io/joson/pics/{{picture}}">
            <img style="width:100%;" src="https://chiyaya.github.io/joson/pics/{{picture}}" is="image">{{firstName}} {{lastName}}</a>
        </li>
      </ul>
    </div>
    <div is="footer" data-role="footer" data-position="fixed" data-theme="b">
      <h3>人力資源部門</h3>
    </div>
  </div>
  <!-- Page: detail  -->
  <div is="page" id="detail" data-role="page">
    <div is="header" data-role="header" data-position="fixed" data-theme="b">
      <h3>個人資料</h3>
      <a is="button" class="ui-btn ui-btn-left" data-rel="back">Back</a>
      <a is="button" class="ui-btn ui-btn-right" data-rel="back">Back</a>
    </div>
    <div is="content" role="main" class="ui-content">
      <img style="width:100%;" src="http://ezoui.com/images/image.png" is="image" id="img">
      <h4><mark>firstName：</mark><span is="span" class="d1"></span></h4>
      <h4><mark>lastName：</mark><span is="span" class="d2"></span></h4>
      <h4><mark>title：</mark><span is="span" class="d3"></span></h4>
      <h4><mark>cellPhone：</mark><span is="span" class="d4"></span></h4>
      <h4><mark>email：</mark><span is="span" class="d5"></span></h4>
      <h4><mark>picture：</mark><span is="span" class="d6"></span></h4>
    </div>
    <div is="footer" data-role="footer" data-position="fixed" data-theme="b">
      <h3>Allen集團人事資料</h3>
    </div>
  </div>
</body>

</html>
