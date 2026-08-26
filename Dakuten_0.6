// ==UserScript==
// @name        Dakuten ⭐
// @namespace        http://tampermonkey.net/
// @version        0.6
// @description        編集枠（通常表示）で濁点・半濁点のチェック　「F10」ダブルキー押下
// @author        Ameba Blog User
// @match        https://blog.ameba.jp/ucs/entry/srventryinsertinput.do*
// @match        https://blog.ameba.jp/ucs/entry/srventryupdateinput.do*
// @icon        https://www.google.com/s2/favicons?sz=64&domain=ameba.jp
// @grant        none
// @updateURL        https://github.com/personwritep/Dakuten/raw/main/Dakuten.user.js
// @downloadURL        https://github.com/personwritep/Dakuten/raw/main/Dakuten.user.js
// ==/UserScript==



let ud_mode; // アンダーライン表示・非表示
ud_mode=localStorage.getItem('Dakuten'); // ストレージ 保存名
if(!ud_mode){
    ud_mode=1; }
localStorage.setItem('Dakuten', ud_mode); // ストレージ 保存



let retry=0;
let interval=setInterval(wait_target, 100);
function wait_target(){
    retry++;
    if(retry>10){ // リトライ制限 10回 1sec
        clearInterval(interval); }
    let target=document.getElementById('cke_1_contents'); // 監視 target
    if(target){
        clearInterval(interval);
        main(); }}



function main(){
    let act_mode=0;
    let buffer;
    let hk; // ハイライト要素のインデックス
    let native_hk; // フォーカス要素のインデックス履歴
    let result_box;
    let count_t;

    let editor_iframe;
    let iframe_doc;
    let iframe_body;
    let iframe_html;

    let target=document.getElementById('cke_1_contents'); // 監視 target
    let monitor=new MutationObserver(catch_key);
    monitor.observe(target, {childList: true}); // ショートカット待受け開始

    catch_key();

    function catch_key(){
        document.onkeydown=function(event){
            check_key(event); }

        editor_iframe=document.querySelector('.cke_wysiwyg_frame');
        if(editor_iframe){
            iframe_doc=editor_iframe.contentWindow.document;
            if(iframe_doc){
                iframe_doc.onkeydown=function(event){
                    check_key(event); }}}


        let clickCount=0;
        function check_key(event){
            if(event.keyCode==121){ //「F10」ダブルキー押下
                event.preventDefault();
                if(!clickCount){ // シングルキー押下の場合
                    ++clickCount;
                    setTimeout( function(){
                        clickCount=0;
                    }, 500 ); }
                else{ // ダブルキー押下の場合
                    clickCount=0;
                    check_act(); }}


            function check_act(){
                if(if_check()){
                    if(act_mode==0){
                        act_mode=1;
                        dis_html(0);
                        setTimeout(()=>{
                            check_text(); }, 20); }
                    else{
                        act_mode=0;
                        dis_html(1);
                        delete_md();
                        remove_container(); }} }

        } // check_key()


        function if_check(){
            editor_iframe=document.querySelector('.cke_wysiwyg_frame');
            if(editor_iframe){
                return true; }
            else{
                return false; }}

        before_end(); // 編集終了時にマークを自動削除

    } // catch_key



    function dis_html(n){
        let editor_tab=document.querySelector('.p-editModeTab');
        if(editor_tab){
            if(n==0){
                editor_tab.style.display='none'; }
            else{
                editor_tab.style.display='block'; }}}



    function disp_container(){
        monitor.disconnect(); // MutationObserverを 起動表示に反応させない
        let insert_div=
            '<div id="cds_container">'+
            '<input type="button" id="unline" value="Underline">'+
            '<span id="cd_result">　</span>'+
            '<style>'+
            '#cds_container { position: absolute; top: 17px; left: 20px; font: 16px Meuryo; '+
            'display: flex; flex-direction: column; '+
            'padding: 4px 3px; background: #fff; '+
            'border: 1px solid #aaa; border-radius: 4px; z-index: 11; } '+
            '#unline { width: 90px; padding: 2px 4px 0px; margin-bottom: 4px; } '+
            '#cd_result { display: inline-block; padding: 4px 6px 2px; '+
            'border: 1px solid #aaa; text-align: center; }'+
            '</style></div>';

        let l_body=document.querySelector('body.l-body');
        if(!l_body.querySelector('#cds_container')){
            l_body.insertAdjacentHTML('beforeend', insert_div); }

        disp_env();

        monitor.observe(target, {childList: true});

    } // disp_container() 「開始処理」



    function remove_container(){
        let cds_container=document.querySelector('#cds_container');
        if(cds_container){
            cds_container.remove(); }}



    function check_text(){
        disp_container();
        change_disp();

        editor_iframe=document.querySelector('.cke_wysiwyg_frame'); // ここで取得
        if(editor_iframe){ //「通常表示」が実行条件
            iframe_doc=editor_iframe.contentWindow.document;
            iframe_body=iframe_doc.querySelector('.cke_editable');
            buffer=iframe_body.innerHTML; // ハイライト表示のためソースコードを保存 🟦

            t_process();

            native_hk=-1;
            hk=0;
            next(hk); }


        function t_process(){
            let search_word=
                ["ぱ","ぴ","ぷ","ぺ","ぽ","ば","び","ぶ","べ","ぼ","パ","ピ","プ","ペ","ポ","バ","ビ","ブ","ベ","ボ"];
            let rep_word;
            let rep_buffer=buffer;
            for(let k=0; k<search_word.length; k++){
                rep_word='<md>'+ search_word[k] +'</md>';
                rep_buffer=rep_buffer.replace(new RegExp(search_word[k], 'g'), rep_word); }

            iframe_body.innerHTML=rep_buffer;
            let md_all=iframe_body.querySelectorAll('md');
            count_t=md_all.length;

            let search_word_p=
                ["ぱ","ぴ","ぷ","ぺ","ぽ","パ","ピ","プ","ペ","ポ"];
            for(let i=0; i<md_all.length; i++){
                if(search_word_p.includes(md_all[i].textContent)){
                    md_all[i].classList.add('pp'); }}}


        function change_disp(){
            let unline=document.querySelector('#unline');
            unline.onclick=function(){
                if(ud_mode==0){
                    ud_mode=1; }
                else{
                    ud_mode=0; }
                localStorage.setItem('Dakuten', ud_mode); // ストレージ 保存
                disp_env(); }}

    } // check_text()



    function disp_env(){
        let unline=document.querySelector('#unline');
        if(ud_mode==0){
            unline.value='Stealth';
            unline.style.filter='';
            add_md_style_nl(); }
        else{
            unline.value='Underline';
            unline.style.filter='sepia(1)';
            add_md_style(); }}



    function next(hk){ //「巡回表示」「選択置換」コード
        result_box=document.querySelector('#cd_result');
        let mark=iframe_body.querySelectorAll('md');

        if(native_hk!=-1){ // 基本的に前回のインデックスを再現🅿
            hk=native_hk; }
        else if(native_hk==-1 || !native_hk){ // 初期インデックス生成🅿
            if(mark.length==1){ hk=0; } // 1個なら即決定
            else{
                let near_n; // 中央後方の要素のインデックス
                let editor_hight=editor_iframe.clientHeight; // 編集枠の高さ
                for(let k=1; k<mark.length; k++){ // スクロール位置中央を越えるmark[k]を取得
                    if(mark[k].getBoundingClientRect().top>editor_hight/2){
                        near_n=k;
                        break; }}
                if(!near_n){ // スクロール位置中央より後方にmark[k]がない場合
                    hk=mark.length-1; }
                else{ // 直前の mark[k]と比較して、近い方を採る
                    if(mark[near_n].getBoundingClientRect().top>
                       editor_hight-mark[near_n-1].getBoundingClientRect().top){
                        hk=near_n-1; }
                    else{
                        hk=near_n; }}}}

        view(hk);
        try{
            mark[hk].classList.add("h"); } // 最初のハイライト色を変更
        catch(e){ ; }

        result_box.textContent=count_t+'│'+(hk+1);

        document.addEventListener("keydown", check_arrow); // documentは先に指定
        iframe_doc=editor_iframe.contentWindow.document;
        if(iframe_doc){
            iframe_doc.addEventListener("keydown", check_arrow); }// iframeは後に指定

        function check_arrow(event){
            if(ud_mode==1){
                if(event.keyCode==38 && act_mode==1){ //「⇧」
                    event.preventDefault();
                    back(); }
                if(event.keyCode==37 && act_mode==1){ //「⇦」
                    event.preventDefault();
                    back(); }
                if(event.keyCode==40 && act_mode==1){ //「⇩」
                    event.preventDefault();
                    forward() }
                if(event.keyCode==39 && act_mode==1){ //「⇨」
                    event.preventDefault();
                    forward() }}



            native_hk=hk;

            function back(){
                if(hk>0){ // 標準のハイライト色に戻す
                    mark[hk].classList.remove("h");
                    hk-=1; }
                else if(hk==0){
                    hk=0; }
                result_box.textContent=count_t+'│'+(hk+1);
                try{
                    mark[hk].classList.add("h"); }
                catch(e){ ; }
                view(hk); }

            function forward(){
                if(hk<mark.length-1){ // 標準のハイライト色に戻す
                    mark[hk].classList.remove("h");
                    hk+=1; }
                else if(hk==mark.length-1){
                    hk=mark.length-1; }
                result_box.textContent=count_t+'│'+(hk+1);
                try{
                    mark[hk].classList.add("h"); }
                catch(e){ ; }
                view(hk); }

        }} // next() インデックス取得🅿



    function view(hk){
        if(ud_mode==1){
            let l_body=document.querySelector('body.l-body');
            let mark=iframe_body.querySelectorAll('md');
            try{
                mark[hk].scrollIntoView({block: "center"});
                iframe_html.scrollBy(0, -12); } // -1～-24  -12がクリープを無くす最適値
            catch(e){ ; }
            l_body.scrollIntoView(); }}



    function add_md_style(){
        editor_iframe=document.querySelector('.cke_wysiwyg_frame');
        if(editor_iframe){ //「通常表示」の場合
            iframe_doc=editor_iframe.contentWindow.document;
            let css_iframe=
                '<style class="epd">'+
                '.cke_editable md { box-shadow: inset 0 -6px 0 -1px #ffcc00; '+
                'display: inline-block; height: 1.5em; } '+ // ハイライト mdタグ背景色⭕
                '.cke_editable md.h { box-shadow: inset 0 -6px 0 -1px red; } '+ // フォーカス mdタグ背景色⭕
                '.cke_editable md.pp { font-family: AmbW; }'+
                '</style>';

            if(iframe_doc.querySelector('.epd')){
                iframe_doc.querySelector('.epd').remove(); }
            iframe_doc.documentElement.insertAdjacentHTML('beforeend', css_iframe); }}


    function add_md_style_nl(){
        editor_iframe=document.querySelector('.cke_wysiwyg_frame');
        if(editor_iframe){ //「通常表示」の場合
            iframe_doc=editor_iframe.contentWindow.document;
            let css_iframe=
                '<style class="epd">'+
                '.cke_editable md.pp { font-family: AmbW; }'+
                '</style>';

            if(iframe_doc.querySelector('.epd')){
                iframe_doc.querySelector('.epd').remove(); }
            iframe_doc.documentElement.insertAdjacentHTML('beforeend', css_iframe); }}


    function delete_md(){
        editor_iframe=document.querySelector('.cke_wysiwyg_frame');
        if(editor_iframe){ //「通常表示」の場合
            iframe_doc=editor_iframe.contentWindow.document;
            iframe_body=iframe_doc.querySelector('.cke_editable');
            if(iframe_body){
                let mark=iframe_body.querySelectorAll('md');
                if(mark.length!=0){
                    iframe_body.innerHTML=
                        iframe_body.innerHTML.replace(new RegExp('<md.*?>', 'g'), ''); }}}}



    function before_end(){
        editor_iframe=document.querySelector('.cke_wysiwyg_frame');
        let submitButton=document.querySelectorAll('.js-submitButton');
        submitButton[0].addEventListener("mousedown", all_clear, false);
        submitButton[1].addEventListener("mousedown", all_clear, false);

        function all_clear(){
            if(!editor_iframe){ //「HTML表示」編集画面の場合
                alert("⛔　Dakuten ⭐ の終了処理ができません\n\n"+
                      "　　 通常表示画面に戻り 編集を終了してください");
                event.stopImmediatePropagation();
                event.preventDefault(); }

            if(editor_iframe){ //「通常表示」編集画面の場合
                if(act_mode==1){
                    dis_html(1);
                    delete_md();
                    remove_container(); }}
        }} // before_end()

} // main()
