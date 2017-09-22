# Animated-menu
animated menu
var animateMenu = (function($) {
    'use strict';

    function listen() {

        $('.opener, .menu-title').click(function() {
            $(".nav-box").toggleClass("opened");
            $("body").toggleClass("menu-opened");
        });
        $(document).mouseup(function(e) {
            var container = $(".menu");
            if (container.has(e.target).length === 0) {
                $("body").removeClass("menu-opened");
                $(".nav-box").removeClass("opened");
            }

        });
        $('.nav-wrap > ul > li:has(ul)').addClass("has-sub");
        $('.nav-wrap > ul > li > .arrow').click(function() {

            var checkElement = $(this).next();

            $('.nav-wrap li').removeClass('active');
            $(this).closest('li').addClass('active');

            if ((checkElement.is('ul')) && (checkElement.is(':visible'))) {
                $(this).closest('li').removeClass('active');
                checkElement.slideUp('normal');
            }

            if ((checkElement.is('ul')) && (!checkElement.is(':visible'))) {
                $('.nav-wrap ul ul:visible').slideUp('normal');
                checkElement.slideDown('normal');
            }

            if (checkElement.is('ul')) {
                return false;
            } else {
                return true;
            }
        });
    }
    return {
        init: listen
    };


}(jQuery));

export default animateMenu;
