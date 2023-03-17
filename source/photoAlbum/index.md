---
title: 相册
date: 2023-03-08 15:37:54
aside: false
top_img: http://43.136.28.91:8899/imageFile/blog/good.jpg
---
<div class="gallery-group-main">
{% galleryGroup '壁纸' '献出心脏塔塔开！！！' 'photoAlbum/girl' https://images8.alphacoders.com/505/505616.png %}
{% galleryGroup '风景' '保留样式暂存' 'photoAlbum/scenery' https://images7.alphacoders.com/130/1306240.jpg %}
{% galleryGroup '坤了' '困了希望看到的' 'photoAlbum/privateAlbum' http://43.136.28.91:8899/imageFile/sese/immortal/no.jpg %}
</div>


<script>
        // 获取第二个 .gallery-group 元素
        var galleryGroup = document.querySelectorAll('.gallery-group')[2];
        
        // 判断是否需要显示图册
        if (document.documentElement.getAttribute('data-theme') === 'dark') {
        // 当前为黑夜模式，并且图册需要在黑夜模式下显示
            galleryGroup.style.display = 'block';
        } else{
            galleryGroup.style.display = 'none';

        }
    




</script>










