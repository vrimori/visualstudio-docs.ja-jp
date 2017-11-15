---
title: "Web ページでのテキストの表示 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, write
- JavaScript, writing text
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8c9ea9d0e0300a0d9b71b0b33d7c99c9ac3935c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="displaying-text-in-a-webpage-javascript"></a>Web ページでのテキストの表示 (JavaScript)
Web ページにテキストを表示する方法は多数あります。 それぞれに長所と短所があり、特定の用途をサポートします。  
  
## <a name="displaying-text"></a>テキストを表示する  
  
-   テキストを表示するために推奨される方法は、要素を作成してその textContent プロパティに書き込むことです。  
  
    ```JavaScript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     この例では、`text` の値は "my text" です。 ただし、親ノードの `textContent` プロパティの取得または設定によって返される値には、ノードの子のテキスト コンテンツが含まれる場合があります。 子ノードに設定された `textContent` が親ノードの `textContent` の値に含まれる例を次に示します。  
  
    ```JavaScript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     この例では、`text` の値は "[nested]" です。  
  
-   また要素を作成して、その [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) または [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) プロパティに書き込むこともできます。 これらのプロパティを設定すると、子ではなく要素自体のテキストのみに影響します。 ただし、これらのプロパティにも短所があります。  
  
    -   [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) プロパティは、動作しないブラウザーがあるため、互換性の理由から回避が必要な場合があります。  
  
    -   [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) プロパティは、CSS スタイルによって影響を受け、要素が非表示の場合は表示されません。  
  
    -   [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) プロパティは、入れ子になったノードとテキストの両方を取得および設定します。 セキュリティで保護されていない場合、スクリプト インジェクション攻撃に使用されることがあります。 さらに、HTML タグなしのテキストに設定すると、前に設定されたすべてのノードが削除されます。  
  
-   `document.write` メソッドは、要素を作成せずに使用できます。 ただし、このメソッドを使用すると Web ページ全体がクリアされるため、望ましくありません。  
  
     `document.write` の使用の短所の例を示します。 このスクリプトは 5 秒ごとに時刻を表示するためのものですが、時刻は 2 回だけ表示されます。 `document.write` が 2 回目に呼び出されるまでに、ページの読み込みは完了しており、`document.write` は、ページ全体をクリアします (`document.open` を呼び出します)。 この時点で、`ShowTime` 関数は既に存在していません。  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     上のコードを修正するには、`document.write` を含むコード行を削除し、それに続く 2 行のコメント行のコメントを解除します。  
  
-   ポップアップ ウィンドウにメッセージを表示する `alert``prompt`、または `confirm` 関数を使用することもできます。 ほとんどの場合、Web ブラウザーでポップアップ ウィンドウを使用することは推奨されません。 ほとんどの最新のブラウザーには、自動的にポップアップ ウィンドウをブロックする設定があり、メッセージが表示されない可能性があります。 さらに、ポップアップ ウィンドウを使用すると無限ループに入る可能性があり、ユーザーが通常の方法で Web ページを閉じることができなくなります。