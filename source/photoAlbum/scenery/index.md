---
title: 相册
date: 2023-03-08 15:37:54
aside: false
top_img: https://images7.alphacoders.com/130/1306240.jpg
---


 <style>
    .carousel-container {
    position: relative;
    overflow: hidden;
    height:30%
    }


    .carousel-wrapper {
    display: flex;
    animation: slide 40s infinite linear;
    }
    
    .carousel-wrapper2 {
    display: flex;
    animation: slide2 40s infinite linear;
    }

    .carousel-item {
    width: 20%;
    margin:10px 10px;
    flex-shrink: 0;
    }

    @keyframes slide {
    0% {
        transform: translateX(0);
    }
    50% {
        transform: translateX(-180%);
    }
    100% {
        transform: translateX(0);
    }
    }

    @keyframes slide2 {
    0% {
        transform: translateX(-180%);
    }
      50% {
        transform: translateX(0);
    }
    100% {
        transform: translateX(-180%);
    }
    }

 </style>
 

 <div id="private-page">
  <!-- 这里是私密内容 -->
   <div class="carousel-container">
  <div class="carousel-wrapper">
    <!-- 动态创建图片 -->
    </div>
    {% timeline %}
    <!-- timeline -->
    这是智能AI生成的图
    <!-- endtimeline -->
    {% endtimeline %}
    </div>
    <div class="carousel-container">
    <div class="carousel-wrapper2">
    <!-- 动态创建图片 -->
    </div>
    </div>
    </div>

  

 <script>

//    var imgUrl = '//43.136.28.91:8899/imageFile/blog/';
    var imgUrl = 'https://s1.ax1x.com/2023/03/20/';
    var images = [
            imgUrl + 'ppNiFm9.jpg', 
            imgUrl + 'ppNiPOJ.jpg', 
            imgUrl + 'ppNiCy4.jpg', 
            imgUrl + 'ppNi9lF.png', 
            imgUrl + 'ppNipSU.png',
            imgUrl + 'ppNPzWT.png', 
            imgUrl + 'ppNPxYV.png', 
            imgUrl + 'ppNPvF0.jpg', 
            imgUrl + 'ppNPXoq.png', 
            imgUrl + 'ppNPOwn.jpg', 
            imgUrl + 'ppNPbLj.jpg', 
            imgUrl + 'ppNPLes.png',
            imgUrl + 'ppNPHyQ.png', 
];
 var images2 = [
            imgUrl + 'ppNiFm9.jpg', 
            imgUrl + 'ppNiPOJ.jpg', 
            imgUrl + 'ppNiCy4.jpg', 
            imgUrl + 'ppNi9lF.png', 
            imgUrl + 'ppNipSU.png',
            imgUrl + 'ppNPzWT.png', 
            imgUrl + 'ppNPxYV.png', 
            imgUrl + 'ppNPvF0.jpg', 
            imgUrl + 'ppNPXoq.png', 
            imgUrl + 'ppNPOwn.jpg', 
            imgUrl + 'ppNPbLj.jpg', 
            imgUrl + 'ppNPLes.png',
            imgUrl + 'ppNPHyQ.png', 

];
    var carouselWrapper = document.querySelector('.carousel-wrapper');
    var carouselWrapper2 = document.querySelector('.carousel-wrapper2');

    // 使用 forEach 遍历 images 数组，并为每个元素创建一个包含图片的 div 元素
    images.forEach((imageUrl) => {
    const imageDiv = document.createElement('div');
    const image = document.createElement('img');
    image.src = imageUrl;
    imageDiv.appendChild(image);
    imageDiv.classList.add('carousel-item');
    carouselWrapper.appendChild(imageDiv);
    });
    images2.forEach((imageUrl) => {
    const imageDiv = document.createElement('div');
    const image = document.createElement('img');
    image.src = imageUrl;
    imageDiv.appendChild(image);
    imageDiv.classList.add('carousel-item');
    carouselWrapper2.appendChild(imageDiv);
    });

    carouselWrapper.addEventListener('mouseenter', () => {
            // 鼠标移入时暂停动画
            carouselWrapper.style.animationPlayState = 'paused';
        });

    carouselWrapper2.addEventListener('mouseenter', () => {
            // 鼠标移入时暂停动画
            carouselWrapper2.style.animationPlayState = 'paused';
        });

    carouselWrapper.addEventListener('mouseleave', () => {
            // 鼠标移入时暂停动画
            carouselWrapper.style.animationPlayState = 'running';
        });

    carouselWrapper2.addEventListener('mouseleave', () => {
            // 鼠标移入时暂停动画
            carouselWrapper2.style.animationPlayState = 'running';
        });

 </script>


  












