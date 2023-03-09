---
title: 相册
date: 2023-03-08 15:37:54
---
  <style>
        #waterfall {
            width: 96%;
            main-height:680px;
            column-count: 5;
            column-gap: 20px;
            margin:0 auto;
        }
        .item {
            position: absolute;
            left: -9999px;
            opacity: 0;
            transition: opacity 3s ease;
            perspective: 1000px;
            cursor: pointer;
            transform: rotateY(0); /* 添加这行代码 */
        }

        .item.show {
            position: static;
            left: auto;
            opacity: 1;
        }
        .item a img {
            width: 100%;
            height: auto;
            transition: transform 1s;
            transform-style: preserve-3d;
        }
        .item:hover a img {
            transform: rotateY(180deg);

        }
       
        .pagination {
            margin-top: 20px;
            text-align: center;
        }

        .pagination a {
            display: inline-block;
            margin-right: 10px;
            padding: 5px 10px;
            border: 1px solid #ccc;
            background-color: #f5f5f5;
            color: #333;
            cursor: pointer;
        }

        .pagination .active {
            background-color: #333;
            color: #fff;
        }


    </style>

  <div id="waterfall"></div>
    <div class="pagination"></div>

 <script>
    const waterfall = document.getElementById('waterfall');
    const images = [
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/avatar.jpg', alt: 'Image 1' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/07753-2023021614112679faa40310b4813f72741f5a9521934bd5d3f132.jpg', alt: 'Image 2' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/201608.jpg', alt: 'Image 2' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/185460.jpg', alt: 'Image 3' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/197924.jpg', alt: 'Image 4' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/169312.jpg', alt: 'Image 6' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/173273.jpg', alt: 'Image 7' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/198378.jpg', alt: 'Image 8' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/215137.jpg', alt: 'Image 9' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/212134.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/212136.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/212132.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/212131.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/212138.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/169310.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/215131.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/215133.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/215134.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/215135.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/215157.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/215136.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/215170.jpg', alt: 'Image 10' },
            { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/215422.jpg', alt: 'Image 10' },
             { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/215423.jpg', alt: 'Image 10' },

            // { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/197924.jpg', alt: 'Image 10' },
            // { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/197924.jpg', alt: 'Image 10' },
            // { url: 'https://cdn.staticaly.com/gh/superxubin/PictureLibrary/main/blog/197924.jpg', alt: 'Image 10' }
        ];

    images.forEach((image, index) => {

            const group = document.createElement('div');
            group.classList.add('item');
            waterfall.appendChild(group);


            const img = document.createElement('img');
            img.src = image.url;
            img.alt = image.alt;

            const lastChild = waterfall.lastChild;
            lastChild.appendChild(img);
        });

        // 获取所有图片元素
        const items = document.querySelectorAll('.item');

        // 每页渲染的图片数量
        const pageSize = 12;

        // 计算总页数
        const pageCount = Math.ceil(items.length / pageSize);

        // 获取页码容器元素
        const pagination = document.querySelector('.pagination');

        // 生成页码
        for (let i = 1; i <= pageCount; i++) {
            const link = document.createElement('a');
            link.textContent = i;
            link.dataset.page = i;
            pagination.appendChild(link);
        }

        // 默认显示第一页
        showPage(1);

        // 添加点击事件监听器
        pagination.addEventListener('click', e => {
            const link = e.target.closest('a');
            if (link) {
                const page = parseInt(link.dataset.page);
                showPage(page);
            }
        });

        // 渲染指定页码的图片
        function showPage(page) {
            // 隐藏所有图片
            items.forEach(item => {
                item.classList.remove('show');
                item.style.opacity = 0;

            });
            // 计算当前页显示的图片范围
            const startIndex = (page - 1) * pageSize;
            const endIndex = Math.min(startIndex + pageSize, items.length);
            // 显示对应页码的图片
            for (let i = startIndex; i < endIndex; i++) {
                // items[i].classList.add('show');
                items[i].style.display = 'inline-block';
                items[i].style.opacity = 1;


            }
            // 设置短暂延迟等待浏览器更新视图
            setTimeout(() => {
                // 将当前页码显示的图片元素显示出来
                for (let i = startIndex; i < endIndex; i++) {
                    // items[i].style.display = 'inline-block';
                    // items[i].style.opacity = 1;

                    items[i].classList.add('show');

                }
                // 将前一页码显示的图片元素隐藏起来
                for (let i = 0; i < startIndex; i++) {
                    // items[i].style.display = 'none';
                    items[i].classList.remove('show');


                    items[i].style.opacity = 0;

                }
                for (let i = endIndex; i < items.length; i++) {
                    // items[i].style.display = 'none';
                    items[i].classList.remove('show');
                    items[i].style.opacity = 0;

                }
            }, 10);
        }


    </script>







