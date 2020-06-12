## Bringing ICCV 2025 to Shenzhen
 
### Executive Summary

* Large computer vision community in Shenzhen and the Greater Bay
Area;

* World-class conference infrastructure secured;
 
* A pleasant place with nice weather, lots of attractions, and
sophisticated cuisine;

* Easy to travel to from around the world, and easy to travel within the Greater Bay area;
 
* Affordable, with family support.
 

### Dynamic Location (地利)

Shenzhen, located at the center of the Greater Bay Area with a population of 70 million in Southern China, is a dynamic city boasting the home to many high-tech businesses and renowned research institutions.  You will have many places to visit during your stay at Shenzhen. If you are a fan of electronic gadgets, there is the world's largest marketplace -- Huaqiangbei. If you'd like to spend a pleasant vacation with your family, you can camp on scenic beaches (Xiaomeisha, Xichong, Dameisha etc.) and stay in luxury beach hotels with gorgeous ocean views.  You will also enjoy the splendid Chinese culture by visiting ancient villages, watching art performances, and enjoying the best food in the captial of dim sum where it is originated known as morning tea. 

Shenzhen is such a dynamic city where traddition and modernity converge.  We sincerely invite you to watch a short video introducing Shenzhen.

#### Youtube.com 

<link rel="stylesheet" type="text/css" href="video-responsive.css" />

<div class="video-responsive">
<iframe width="1280" height="715" src="https://www.youtube.com/embed/kahd3KmNsOE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

#### Bilibili.com (within China)

<div class="video-responsive">
<iframe width="1280" height="715" src="//player.bilibili.com/player.html?aid=19348684&bvid=BV1sW411n7EJ&cid=31553075&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</div>

### Delightful Weather (天时)

The proposed conference is scheduled to be a seven-day event, beginning 14 December 2025 through 20 December 2025. Shenzhen has a very pleasant winter in this period, with an average temperature of 65°F or 18°C in December.  You will have an enjoyable holiday season travel to Shenzhen, and have the chance to visit many dynamic cities such as Gangzhou (29 min by train), Hong Kong (18 min by train) and Macau and Zhuhai (by ferry, or via the HZM bridge, the world's longest sea crossing bridge of 34 miles) in the Greater Bay Area. 

These vivid cities are closely connnected via a world-class high-speed train system, making traveling in the Greater Bay Area super easy, comfortable and affordable. You will have an unforgettable holiday with your family and significant ones, welcoming the new year of 2026 together in Shenzhen's best beach hotels, on the Pearl River night cruise of Guangzhou, in the Disneyland theme park of Hong Kong, or in the Sands' landmark casino hotels of Macau.

### Diverse Team (人和)

We present a diverse organizing team that already covers the key roles, including three honorary Chairs, four General Chairs, five Program Chairs, two Finance Chairs and three Local Arrangement Chairs from the Americas, Asia-Pacific Region and Europe. Young talents are well represented on the team, who will work closely with the senior members in organizing the conference and preparing a high-quality program. Other organizing committee members will be filled in later, again according to the principle of diversity.


## Our proposal

You are sincerely invited to download and read our proposal [(high resolution, 15MB)](http://iccv2025shenzhen.github.io/ICCV2025shenzhen.pdf) and [(low resolution, 6MB)](http://iccv2025shenzhen.github.io/ICCV2025shenzhen_compact.pdf) for ICCV 2025 at Shenzhen.

You can click on the following photo to view it online without downloading it.

<div class="pdf-container">
  <embed width="100%" height="400" src="ICCV2025shenzhen_v1.pdf" type="application/pdf" fullscreen="yes">
</div>


<div style="background:#404040">
    <p/>
    <div style="background:#404040">
        <div style="text-align:center;margin-top:10px">
            <canvas id="the-canvas"></canvas>
        </div>
    </div>
    <div style="text-align:center">
        <button id="prev">上一页</button>
        <button id="next">下一页</button>
    </div>
</div>

<canvas id="the-canvas"></canvas>
<script src="pdf.js"></script>
<script src="pdf.worker.js"></script>
<script>
        //引入pdf.js之后
        var url = 'ICCV2025shenzhen_v1.pdf';
        PDFJS.workerSrc = 'pdf.worker.js';
        //定义变量
        var pdfDoc = null,
            pageNum = 1,
            pageRendering = false,
            pageNumPending = null,
            scale = 1,
            canvas = document.getElementById('the-canvas'),
            ctx = canvas.getContext('2d');
        function renderPage(num) {
            pageRendering = true;
            pdfDoc.getPage(num).then(function (page) {
                //设置页面大小
                var viewport = page.getViewport(1);
                console.log(viewport.width);
                var desiredWidth = "500";
                var scale = desiredWidth / viewport.width;
                scale=0.65;
                var scaledViewport = page.getViewport(scale);
                //var viewport = page.getViewport(scale);
                canvas.height = scaledViewport.height;
                canvas.width = scaledViewport.width;
                //设置背景颜色(无效)
                canvas.style.backgroundColor = "red";
                //进行文件读取加载
                var renderContext = {
                    canvasContext: ctx,
                    viewport: scaledViewport
                };
                var renderTask = page.render(renderContext);
                renderTask.promise.then(function () {
                    pageRendering = false;
                    if (pageNumPending !== null) {
                        // New page rendering is pending
                        renderPage(pageNumPending);
                        pageNumPending = null;
                    }
                });
            });
            //显示总页数
            document.getElementById('page_num').textContent = pageNum;
        }
                        //翻页方法
        function queueRenderPage(num) {
            if (pageRendering) {
                pageNumPending = num;
            } else {
                renderPage(num);
            }
        }
        function onPrevPage() {
            if (pageNum <= 1) {
                return;
            }
            pageNum--;
            queueRenderPage(pageNum);
        }
        //上一页监听
        document.getElementById('prev').addEventListener('click', onPrevPage);
        function onNextPage() {
            if (pageNum >= pdfDoc.numPages) {
                return;
            }
            pageNum++;
            queueRenderPage(pageNum);
        }
        //下一页监听
        document.getElementById('next').addEventListener('click', onNextPage);
        PDFJS.getDocument(url).then(function (pdfDoc_) {
            pdfDoc = pdfDoc_;
            document.getElementById('page_count').textContent = pdfDoc.numPages;
            renderPage(pageNum);
        });
</script>


## Questions?

Having questions about our proposal? Email us at iccv2025@gmail.com and we are looking forward to hearing your opinions and suggestions about our proposal.

