원문 : [http://lab.abhinayrathore.com/jquery-standards/](http://lab.abhinayrathore.com/jquery-standards/)

#Loading jQuery jQuery 로딩하기

 1.Always try to use a CDN to include jQuery on your page. [CDN Benefits](http://www.sitepoint.com/7-reasons-to-use-a-cdn/) 여러분의 페이지에 jQuery를 삽입할 때 항상 CDN을 사용하도록 하십시요. [CDN을 사용해야하는 7가지 이유](http://www.sitepoint.com/7-reasons-to-use-a-cdn/) 

    <script type="text/javascript" src="//ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
    <script>window.jQuery || document.write('<script src="js/jquery-2.1.1.min.js" type="text/javascript"><\/script>')</script>

[여기](http://lab.abhinayrathore.com/jquery-standards/#jQueryCND)에 가장 인기있는 jQuery CDN 리스트가 있습니다.

2. Implement a fallback to your locally hosted library of same version as shown above. [More Info](http://css-tricks.com/snippets/jquery/fallback-for-cdn-hosted-jquery/) 위의 예시처럼 여러분의 로컬 호스트에 동일한 버전의 대체 코드를 마련해두는 것이 좋습니다. [더 보기](http://css-tricks.com/snippets/jquery/fallback-for-cdn-hosted-jquery/)

3. Use [protocol-relative/protocol-independent](http://www.paulirish.com/2010/the-protocol-relative-url/) URL (leave http: or https: out) as shown above. 위 예시 처럼 [상대적 프로토콜](http://www.paulirish.com/2010/the-protocol-relative-url/) URL(http:또는 https:를 제거)을 사용하십시요.

4. If possible, keep all your JavaScript and jQuery includes at the bottom of your page.[More Info ](http://developer.yahoo.com/blogs/ydn/high-performance-sites-rule-6-move-scripts-bottom-7200.html) and a sample on [HTML5 Boilerplate ](https://github.com/h5bp/html5-boilerplate/blob/master/index.html). 가능하다면, 자바스크립트와 제이쿼리 파일들을 페이지 하단에 삽입하십시요. [더 많은 정보](http://developer.yahoo.com/blogs/ydn/high-performance-sites-rule-6-move-scripts-bottom-7200.html) 그리고 [HTML5 Boilerplate ](https://github.com/h5bp/html5-boilerplate/blob/master/index.html)

5. What version to use? 어떤 버전을 사용해야하나?

- DO NOT use jQuery version 2.x if you support Internet Explorer 6/7/8. 만약 여러분이 인터넷 익스플로러 6/7/8을 지원해야 한다면 2.x 버전을 사용하지 마십시요. 

- For new web-apps, if you do not have any plugin compatibility issue, it's highly recommended to use the latest jQuery version. 호환성 이슈가 있는 플러그인을 사용하지 않는 새로운 앱의 경우 가장 최신 버전을 사용하는 것을 강하게 권합니다.

- When loading jQuery from CDN's, always specify the complete version number you want to load (Example: _1.11.0_ as opposed to _1.11_ or just    _1_). CDN을 통해 제이쿼리를 로딩하고자 할때 항상 정확한 버전의 숫자를 기입하십시오(예: _1.11.0_ as opposed to _1.11_ or just    _1_).

- DO NOT load multiple jQuery versions. 여러개의 버전을 동시에 로드하지 마십시오.

- DO NOT use [jquery-latest.js from jQuery CDN](http://blog.jquery.com/2014/07/03/dont-use-jquery-latest-js/). 제이쿼리 CDN으로 로드하고자 할때 [jquery-latest.js](http://blog.jquery.com/2014/07/03/dont-use-jquery-latest-js/)를 사용하지 마십시요.

6 If you are using other libraries like Prototype, MooTools, Zepto etc. that uses $ sign as well, try not to use $ for calling jQuery functions and instead use jQuery simply. You can return control of $ back to the other library with a call to $.noConflict(). 만약 $ 표시를 사용하는 Protorype, MooTools, Zepto 등과 같은 라이브러리와 함께 사용한다면 제이쿼리 함수를 호출하기 위해 $를 사용하는 대신 jQuery를 사용하십시요. $.noConflict()를 호출함으로서 $의 제어를 다른 라이브러리에게 양보할 수 있습니다.

7. For advanced browser feature detection, use [Modernizr](http://modernizr.com/). 고급 브라우저 기능 탐지를 할 수 있는 [Modernizr](http://modernizr.com/)를 사용하십시요.

# jQuery Variables 제이쿼리 변수

1. All variables that are used to store/cache jQuery objects should have a name prefixed with a $. 제이쿼리 객체로 저장/캐쉬 하기위해 사용되는 모든 변수는 이름 앞에 $가 있어야 합니다.

2. Always cache your jQuery selector returned objects in variables for reuse. 재사용을 위해 항상 객체를 반환하는 제이쿼리 선택자를 변수에 담아 사용하십시요.
    
    var $myDiv = $("#myDiv");
    $myDiv.click(function(){...});

3. Use [camel case ](http://en.wikipedia.org/wiki/CamelCase) for naming variables. 변수의 이름은 [캐멀 케이스 표기법](http://en.wikipedia.org/wiki/CamelCase)을 사용하십시요.

# Selectors 선택자

1. Use ID selector whenever possible. It is faster because they are handled using document.getElementById(). 가능하면 ID 선택자를 사용하세요. document.getElementById()를 이용하여 처리하기 때문에 더 빠릅니다.

2. When using class selectors, don't use the element type in your selector.[Performance Comparison 성능비교 ](http://jsperf.com/jqeury-selector-test) 클래스 선택자를 사용할 때에는 선택자의 요소 타입을 쓰지 마십시요.

    var $products = $("div.products"); // SLOW
    var $products = $(".products"); // FAST

3. Use find for _Id->Child_ nested selectors. The .find() approach is faster because the first selection is handled without going through the Sizzle selector engine. [More Info ](http://learn.jquery.com/performance/optimize-selectors/) Id의 자식 내 집합을 선택하기 위해서 find를 사용하세요. 아래 예제에서 볼 수 있듯이 아이디 선택자는 Sizzle 선택자 엔진(제이쿼리가 사용하는 선택자 엔진)을 거치지 않기 때문에 .find()로 접근하는 것이 더 빠릅니다. [더 보기 ](http://learn.jquery.com/performance/optimize-selectors/)


    // BAD, a nested query for Sizzle selector engine
    var $productIds = $("#products div.id");

    // GOOD, #products is already selected by document.getElementById() so only div.id needs to go through Sizzle selector engine. #products는 이미 document.getElementById() 에 의해서 선택되어 지므로 div.id에만 Sizzle selector engine을 거칩니다.
    var $productIds = $("#products").find("div.id");


4. Be specific on the right-hand side of your selector, and less specific on the left. [More Info ](http://learn.jquery.com/performance/optimize-selectors/) 오른쪽편에 사용할 선택자를 명시하고 나머지는 왼쪽에 위치시킵니다.(가능하면 가장 오른쪽에는 tag.class형식으로 쓰고 왼쪽에는 그냥 tag나 .class를 쓰세요.) [더 보기 ](http://learn.jquery.com/performance/optimize-selectors/) 

    // Unoptimized
    $("div.data .gonzalez");

    // Optimized
    $(".data td.gonzalez");

5. Avoid Excessive Specificity. [More Info ](http://learn.jquery.com/performance/optimize-selectors/),    [Performance Comparison ](http://jsperf.com/avoid-excessive-specificity) 복잡한 표현 방식은 피합니다. [더 보기 ](http://learn.jquery.com/performance/optimize-selectors/), [성능 비교 ](http://jsperf.com/avoid-excessive-specificity)

    $(".data table.attendees td.gonzalez");

    // Better: Drop the middle if possible.
    $(".data td.gonzalez");

6. Give your Selectors a Context. 선택자에 범위를 기제합니다.

    // SLOWER because it has to traverse the whole DOM for .class DOM전체에서 .class를 찾습니다.
    $('.class');

    // FASTER because now it only looks under class-container. class-container의 범위 안에서 찾습니다.
    $('.class', '#class-container');

7. Avoid Universal Selectors. [More Info ](http://learn.jquery.com/performance/optimize-selectors/) 유니버셜 선택자(*) 사용을 피합니다. [더 보기 ](http://learn.jquery.com/performance/optimize-selectors/)

    $('div.container > *'); // BAD
    $('div.container').children(); // BETTER

8. Avoid Implied Universal Selectors. When you leave off the selector, the universal selector (*) is still implied. [More Info ](http://learn.jquery.com/performance/optimize-selectors/) 암시적인 전체 선택자는 피합니다. 셀렉터를 누락시켰을 때, 전체 선택자(*)를 여전히 내포하게 됩니다. [더 보기 ](http://learn.jquery.com/performance/optimize-selectors/)

    $('div.someclass :radio'); // BAD, $( ".category *:radio" )와 같습니다.
    $('div.someclass input:radio'); // GOOD

9. Don’t Descend Multiple IDs or nest when selecting an ID. ID-only selections are handled using document.getElementById() so don't mix them with other selectors. ID를 선택할 때 중복 또는 다중 선택하지 마세요. document.getElementById를 사용하여 처리되기 때문에 다른선택자와 혼용하지말고 오직 ID선택자만 사용합니다. 

    $('#outer #inner'); // BAD
    $('div#inner'); // BAD
    $('.outer-container #inner'); // BAD
    $('#inner'); // GOOD, only calls document.getElementById()


# DOM Manipulation DOM 조작

1. Always detach any existing element before manipulation and attach it back after manipulating it.    [More Info ](http://learn.jquery.com/performance/detach-elements-before-work-with-them/)  항상 조작하기 전에 기존 요소를 분리하고 조작 후 다시 연결합니다.  [더 보기 ](http://learn.jquery.com/performance/detach-elements-before-work-with-them/)

    var $myList = $("#list-container > ul").detach();
    //...a lot of complicated things on $myList
    $myList.appendTo("#list-container");


2. Use string concatenation or array.join() over .append(). [More Info ](http://learn.jquery.com/performance/append-outside-loop/)
Performance comparison: [http://jsperf.com/jquery-append-vs-string-concat ](http://jsperf.com/jquery-append-vs-string-concat)  .append() 보다 array.join() 또는 문자열 연결을 사용하세요.  [더 보기 ](http://learn.jquery.com/performance/append-outside-loop/)
성능 비교: [http://jsperf.com/jquery-append-vs-string-concat](http://jsperf.com/jquery-append-vs-string-concat) 

    // BAD
    var $myList = $("#list");
    for(var i = 0; i < 10000; i++){
        $myList.append("<li>"+i+"</li>");
    }

    // GOOD
    var $myList = $("#list");
    var list = "";
    for(var i = 0; i < 10000; i++){
        list += "<li>"+i+"</li>";
    }
    $myList.html(list);

    // EVEN FASTER
    var array = [];
    for(var i = 0; i < 10000; i++){
        array[i] = "<li>"+i+"</li>";
    }
    $myList.html(array.join(''));

3. Don’t Act on Absent Elements. [More Info ](http://learn.jquery.com/performance/dont-act-on-absent-elements/)  요소의 존재를 확인하고 실행하세요. [더 보기 ](http://learn.jquery.com/performance/dont-act-on-absent-elements/) 

    //BAD: This runs three functions before it realizes there's nothing in the selection 선택된 것이 없다는 것을 알기전에 세 개의 함수가 실행됩니다.
    $("#nosuchthing").slideUp();
   
    //GOOD
    var $mySelection = $("#nosuchthing");
    if ($mySelection.length) {
        $mySelection.slideUp();
    }

# Events

1. Use only one Document Ready handler per page. It makes it easier to debug and keep track of the behavior flow. 하나의 페이지에서는 Document Ready 핸들러를 한 번만 사용하십시요. 디버깅을 더 쉽게해주고 동작의 흐름을 추적할 수 있습니다.

2. DO NOT use anonymous functions to attach events. Anonymous functions are difficult to debug, maintain, test, or reuse. [More Info ](http://learn.jquery.com/code-organization/beware-anonymous-functions/) 이벤트에 익명함수를 사용하지 마십시오. 익명함수는 디버깅, 유지보수, 테스트 또는 재사용을 어렵게 합니다.

    $("#myLink").on("click", function(){...}); // BAD
    
    // GOOD
    function myLinkClickHandler(){...}
    $("#myLink").on("click", myLinkClickHandler);

3. Document ready event handler should not be an anonymous function. Once again, anonymous functions are difficult to debug, maintain, test, or reuse. Document ready 이벤트 핸들러를 익명함수로 만들지 마십시오. 다시말하지만 익명함수는 디버깅, 유지보수, 테스트 또는 재사용을 어렵게 합니다.

    $(function(){ ... }); // BAD: You can never reuse or write a test for this function. 이 함수를 결코 재사용할 수 없거나 테스트로 작성할 수 없습니다.
    
    // GOOD
    $(initPage); // or $(document).ready(initPage);
    function initPage(){
        // Page load event where you can initialize values and call other initializers. 
    }

4. Document ready event handlers should be included from external files and inline JavaScript can be used to call the ready handle after any initial setup. Document ready 이벤트 핸들러를 외부 파일로 삽입시킬 수도 있습니다. 그리고 인라인 자바스크립트는 초기 설정 후 ready 핸들을 호출하는 데 사용할 수 있습니다.

    <script src="my-document-ready.js"></script>
    <script>
        // Any global variable set-up that might be needed.
        $(document).ready(initPage); // or $(initPage);
    </script>

5. DO NOT use behavioral markup in HTML (JavaScript inlining), these are debugging nightmares. Always bind events with jQuery to be consistent so it's
easier to attach and remove events dynamically. HTML에 동적 마크업을 사용하지 마십시오(JavaScript inlining), 이것은 디버깅의 악몽입니다. 항상 일관되게 제이쿼리로 이벤트를 바인드하면 이벤트를 동적으로 붙이거나 제거하기 쉽습니다.

    <a id="myLink" href="#" onclick="myEventHandler();">my link</a> <!-- BAD -->
    $("#myLink").on("click", myEventHandler); // GOOD

6. When possible, use custom [namespace](http://api.jquery.com/event.namespace/) for events. It's easier to unbind the exact
event that you attached without affecting other events bound to the DOM element. 가능하면 이벤트의 [네임스페이스](http://api.jquery.com/event.namespace/)를 커스텀하여 사용하십시오. 돔 엘리먼트에 연결된 다른 이벤트에 영향을 주도록 붙여놓은 이벤트를 정확하게 해제하기가 쉽습니다.

    $("#myLink").on("click.mySpecialClick", myEventHandler); // GOOD
    // Later on, it's easier to unbind just your click event
    $("#myLink").unbind("click.mySpecialClick");

7. Use [event delegation](http://learn.jquery.com/events/event-delegation/) when you have to attach same event to multiple
elements. Event delegation allows us to attach a single event listener, to a parent element, that will fire for all descendants matching a selector,
whether those descendants exist now or are added in the future. 여러 요소에 같은 이벤트를 붙이려 할때에는 [이벤트 위임](http://learn.jquery.com/events/event-delegation/)을 사용하십시오. 이벤트 위임은 하나의 부모 엘리먼트에 하나의 이벤트 리스터 만을 붙이며 이것으로 선택자와 매칭되는 모든 자손에게(그 자손이 지금 존재하든지 미래에 추가되던지 간에) 이벤트가 일어나게 됩니다. 

    $("#list a").on("click", myClickHandler); // BAD, you are attaching an event to all the links under the list.
    $("#list").on("click", "a", myClickHandler); // GOOD, only one event handler is attached to the parent.

# Ajax 아작스

1. Avoid using _.getJson()_ or _.get()_, simply use the $.ajax() as that's what gets called internally. _.getJson()_이나 _.get()_의 사용을 피하고 $.ajax()를 사용하십시요.

2. DO NOT use _http_ requests on _https_ sites. Prefer schemaless URLs (leave the protocol _http/https_ out of your URL) _https_ 사이트에서 _http_를 사용하지 마십시오. 스키마 없는 URL을 더 선호합니다.(여러분의 URL에서 _http/https_ 프로토콜을 제거하세요.)

3. DO NOT put request parameters in the URL, send them using data object setting. request 파라미터에 붙이지 말고 데이터 객체 설정을 사용하여 전달하십시오. 

    // Less readable...
    $.ajax({
        url: "something.php?param1=test1&amp;param2=test2",
        ....
    });

    // More readable...
    $.ajax({
        url: "something.php",
        data: { param1: test1, param2: test2 }
    });

4. Try to specify the _dataType_ setting so it's easier to know what kind of data you are working with. (See Ajax Template example below) _dataType_을 기입하는 것이 좋습니다. 어떤 종류의 데이터가 오고가는지 알기 더 쉽습니다.

5. Use Delegated event handlers for attaching events to content loaded using Ajax. Delegated events have the advantage that they can process events from
descendant elements that are added to the document at a later time (example Ajax). [More Info ](http://api.jquery.com/on/#direct-and-delegated-events) Ajax로 로딩된 컨텐츠에 이벤트를 붙이기 위해서 위임된 이벤트 핸들러를 사용하세요. 위임된 이벤트는 나중에 document에 추가된 자식요소들에게도 이벤트를 진행시킬 수 있는 이점이 있습니다.

    $("#parent-container").on("click", "a", delegatedClickHandlerForAjax);

6. Use Promise interface: [More Examples](http://www.htmlgoodies.com/beyond/javascript/making-promises-with-jquery-deferred.html) Promise 인터페이스를 사용하세요: [예제 더 보기](http://www.htmlgoodies.com/beyond/javascript/making-promises-with-jquery-deferred.html)

    $.ajax({ ... }).then(successHandler, failureHandler);

    // OR
    var jqxhr = $.ajax({ ... });
    jqxhr.done(successHandler);
    jqxhr.fail(failureHandler);

7. Sample Ajax Template: [More Info ](https://api.jquery.com/jQuery.ajax/) Ajax 템플릿 샘플: [더 보기](https://api.jquery.com/jQuery.ajax/) 

    var jqxhr = $.ajax({
        url: url,
        type: "GET", // default is GET but you can use other verbs based on your needs.
        cache: true, // default is true, but false for dataType 'script' and 'jsonp', so set it on need basis.
        data: {}, // add your request parameters in the data object.
        dataType: "json", // specify the dataType for future reference
        jsonp: "callback", // only specify this to match the name of callback parameter your API is expecting for JSONP requests.
        statusCode: { // if you want to handle specific error codes, use the status code mapping settings.
            404: handler404,
            500: handler500
        }
    });
    jqxhr.done(successHandler);
    jqxhr.fail(failureHandler);


# Effects and Animations 효과와 애니메이션

1. Adopt a restrained and consistent approach to implementing animation functionality. 애니메이션 기능을 구현하기위해 절제되고 일관된 접근 방법을 채택하십시오.

2. DO NOT over-do the animation effects until driven by the UX requirements. UX 요구사항이 있기 전에 애니메이션 효과를 과도하게 하지 마십시오.

- Try to use simeple show/hide, toggle and slideUp/slideDown functionality to toggle elements. 토글 요소를 위해 show/hide, toggle 그리고 slideUp/slideDown 과 같이 간단한 기능을 사용하는것이 좋습니다.

- Try to use predefined animations durations of "slow", "fast" or 400 (for medium). 미리정의된 애니메이션 속도인 "slow", "fast"를 사용하거나 중간속도를 위해서는 400을 사용하는 것이 좋습니다.

# Plugins 플러그인

1. Always choose a plugin with good support, documentation, testing and community support. 플러그인을 선택할 때는 기술지원, 문서, 테스트 그리고 커뮤니티가 좋은지 따져 선택하십시오.

2. Check the compatibility of plugin with the version of jQuery that you are using. 플러그인이 여러분이 사용하는 제이쿼리 버전과 호환되는지 체크하십시오.

3. Any common reusable component should be implemented as a jQuery plugin. [Click here](http://lab.abhinayrathore.com/jquery-standards/#jQueryPluginBoilerplate) for jQuery Plugin Boilerplate code. 어떤 공통의 재사용가능한 컴포넌트는 제이쿼리 플러그인으로 구현되야 합니다. [더 보기](http://lab.abhinayrathore.com/jquery-standards/#jQueryPluginBoilerplate)

# Chaining 체인

1. Use chaining as an alternative to variable caching and multiple selector calls. 변수를 저장하고 동시에 여러 선택자를 호출하기위한 대안으로 체인을 사용하십시오.

    $("#myDiv").addClass("error").show();

2. Whenever the chain grows over 3 links or gets complicated because of event assignment, use appropriate line breaks and indentation to make the code
readable. 체인의 링크가 3개가 넘거나 이벤트 할당으로 복잡해지면 줄바꿈을 하고 들여쓰기를 통해 가독성을 높이십시요.

    $("#myLink")
        .addClass("bold")
        .on("click", myClickHandler)
        .on("mouseover", myMouseOverHandler)
        .show();

3. For long chains it is acceptable to cache intermediate objects in a variable. 긴 체인으로 변수에 중간 객체를 캐쉬하는 것이 가능해집니다.

# Miscellaneous 기타

1. Use Object literals for parameters. 복수의 파라미터는 객체 표현식을 사용하십시오.

    $myLink.attr("href", "#").attr("title", "my link").attr("rel", "external"); // BAD, 3 calls to attr()

    // GOOD, only 1 call to attr()
    $myLink.attr({
        href: "#",
        title: "my link",
        rel: "external"
    });

2. Do not mix CSS with jQuery. 제이쿼리에 CSS를 혼용하지 마십시오.

    $("#mydiv").css({'color':red, 'font-weight':'bold'}); // BAD

    .error { color: red; font-weight: bold; } /* GOOD */
    $("#mydiv").addClass("error"); // GOOD

3. DO NOT use Deprecated Methods. It is always important to keep an eye on deprecated methods for each new version and try avoid using them. [Click here ](http://api.jquery.com/category/deprecated/) for a list of deprecated methods. 비추천 메소드를 사용하지 마십시오. 새 버전이 나올때 마다 비추천된 메소드가 있는지 주의깊게 살펴보고 그것들을 사용하지 않도록 하십시오. [비추천 메소드 리스트](http://api.jquery.com/category/deprecated/)

4. Combine jQuery with native JavaScript when needed. See the performance difference for the example given below: [http://jsperf.com/document-getelementbyid-vs-jquery/3 ](http://jsperf.com/document-getelementbyid-vs-jquery/3) 필요하다면 기본 자바스크립트 코드와 제이쿼리를 함께 사용하십시요. 아래 주어진 예제에서 성능차이를 보십시요 : [http://jsperf.com/document-getelementbyid-vs-jquery/3 ](http://jsperf.com/document-getelementbyid-vs-jquery/3)

    $("#myId"); // is still little slower than...
    document.getElementById("myId");

# Resources 자료

* 제이쿼리 성능: http://learn.jquery.com/performance/ ](http://learn.jquery.com/performance/)
* 제이쿼리 학습: [http://learn.jquery.com ](http://learn.jquery.com/)
* 제이쿼리 API 문서: [http://api.jquery.com/ ](http://api.jquery.com/)
* 제이쿼리 Coding Standards and Best Practice: [http://www.jameswiseman.com/blog/2010/04/20/jquery-standards-and-best-practice/](http://www.jameswiseman.com/blog/2010/04/20/jquery-standards-and-best-practice/)
* 제이쿼리 Cheatsheet: [http://lab.abhinayrathore.com/jquery-cheatsheet/](http://lab.abhinayrathore.com/jquery-cheatsheet/)
* 제이쿼리 플러그인 표준코드:[http://stefangabos.ro/jquery/jquery-plugin-boilerplate-revisited/](http://stefangabos.ro/jquery/jquery-plugin-boilerplate-revisited/)
