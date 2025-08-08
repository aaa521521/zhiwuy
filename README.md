<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>页面重定向</title>
    <style>
        html, body {
            width: 100% !important;
            height: 100% !important;
            margin: 0 !important;
            padding: 0 !important;
            overflow: hidden !important;
            background-color: #000;
        }
        
        #contentFrame {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            margin: 0 !important;
            padding: 0 !important;
            border: none !important;
            outline: none !important;
            box-shadow: none !important;
            background-color: #000;
            overflow: hidden;
        }

        @media screen and (max-width: 600px) {
            html, body {
                -webkit-touch-callout: none;
                -webkit-user-select: none;
                -moz-user-select: none;
                -ms-user-select: none;
                user-select: none;
            }
        }
        
        /* 添加加载提示样式 */
        #loadingText {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: #aaa;
            font-family: Arial, sans-serif;
            z-index: 100;
        }
    </style>
    <script>
        window.onload = function() {
            // 直接设置固定目标链接
            const TARGET_URL = "https://vip.fmkefu.com/c/";
            
            const frame = document.getElementById('contentFrame');
            const loadingText = document.getElementById('loadingText');
            
            // 显示加载提示
            loadingText.textContent = "正在加载页面...";
            
            // 设置iframe源
            frame.src = TARGET_URL;
            
            // 调整iframe尺寸
            frame.style.width = window.innerWidth + 'px';
            frame.style.height = window.innerHeight + 'px';
            
            // 加载完成后隐藏提示
            frame.onload = function() {
                loadingText.style.display = 'none';
            };
        };
        
        // 动态调整尺寸
        window.addEventListener('resize', function() {
            const frame = document.getElementById('contentFrame');
            frame.style.width = window.innerWidth + 'px';
            frame.style.height = window.innerHeight + 'px';
        });
        
        // 阻止手势缩放
        document.addEventListener('touchstart', function(e) {
            if (e.touches.length > 1) e.preventDefault();
        }, { passive: false });

        document.addEventListener('gesturestart', function(e) {
            e.preventDefault();
        });
    </script>
</head>
<body>
    <!-- 加载提示元素 -->
    <div id="loadingText"></div>
    
    <iframe 
        id="contentFrame" 
        frameborder="0"
        scrolling="yes"
        allowfullscreen
        sandbox="allow-same-origin allow-scripts"
        style="display:block;"></iframe>
</body>
</html>
