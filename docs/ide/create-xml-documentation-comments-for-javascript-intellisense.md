---
title: "方法: JavaScript XML ドキュメントのコメントを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コードのコメント, JavaScript IntelliSense"
  - "ドキュメント コメント [JavaScript]"
  - "IntelliSense [JavaScript], XML ドキュメント コメント"
  - "XML ドキュメント コメント, JavaScript IntelliSense"
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法: JavaScript XML ドキュメントのコメントを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*XML ドキュメントのコメント* JavaScript のコメント、スクリプト、関数、フィールド、変数などのコード要素に関する情報を提供するために追加されます。  スクリプト関数を参照すると Visual Studio では、これらのテキストの説明に IntelliSense が表示されます。  
  
 このトピックは、XML ドキュメントのコメントを使用して基本的なチュートリアルを示します。  などの他の要素を使用する方法については[\<var\>](../ide/var-javascript.md)と[\<value\>](../ide/value-javascript.md)、およびその他のコード例についてを参照してください[XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)。  などの IntelliSense については、非同期のコールバックを提供することの詳細については、 `Promise`を参照してください[\<returns\>](../ide/returns-javascript.md)。  
  
> [!NOTE]
>  XML ドキュメント コメントは、参照されるファイル、アセンブリ、およびサービスからのみ利用できます。  
  
### XML ドキュメントのコメントの JavaScript 関数を作成するのには  
  
-   この関数では、追加[\<summary\>](../ide/summary-javascript.md)、 [\< param \>](../ide/param-javascript.md)、および[\<returns\>](../ide/returns-javascript.md)要素、各要素には、次の 3 つのスラッシュ \(\/\/\/\) よりも前。  
  
    > [!NOTE]
    >  各要素は 1 行で必要があります。  
  
     次の例では、JavaScript の関数を示しています。  
  
    ```javascript  
    function getArea(radius)  
    {  
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>  
        /// <param name="radius" type="Number">The radius of the circle.</param>  
        /// <returns type="Number">The area.</returns>  
        var areaVal;  
        areaVal = Math.PI * radius * radius;  
        return areaVal;  
    }  
    ```  
  
-   XML ドキュメントのコメントを表示するには、名前には、次の例のように、XML ドキュメントのコメントが付いている関数のかっこを入力します。  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     XML ドキュメントのコメントが含まれている関数の左かっこを入力すると、コード エディターは、XML ドキュメント コメントで定義されている情報を表示するのに IntelliSense を使用します。  
  
### XML ドキュメント コメントは JavaScript を作成するには  
  
-   コンス トラクターの関数またはオブジェクトの定義に追加する、 [\<field\>](../ide/field-javascript.md)要素の前での 3 つのスラッシュ \(\/\/\/\)。  
  
     使用例を示します、 `<field>` 、コンス トラクター関数内の要素。  その他の例については、「[\<field\>](../ide/field-javascript.md)」を参照してください。  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   XML ドキュメントのコメントを表示するには、マークされている、function コンス トラクターを使用して、次の例のように、XML ドキュメントのコメントをオブジェクトを作成します。  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   次の行には、オブジェクトおよび IntelliSense については、フィールドを表示するには、期間の名前を入力します。  
  
    ```javascript  
    eng.  
    ```  
  
### XML ドキュメント コメントは、オーバー ロードされた関数を作成するのには  
  
1.  この関数には、追加、 [\<signature\>](../Topic/%3Csignature%3E%20\(JavaScript\).md)要素の各オーバー ロードします。  など、他の要素では、これらの要素を追加`<summary>`、 `<param>`、および`<returns>`、前の各要素には、次の 3 つのスラッシュ \(\/\/\/\)。  
  
     次の使用例は、オーバー ロードされた JavaScript の関数を示しています。  この例では、パラメーターの型でオーバー ロードとは異なります。  
  
    ```javascript  
    function calc(a) {  
        /// <signature>  
        /// <summary>Function summary 1.</summary>  
        /// <param name="a" type="Number">A number.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        /// <signature>  
        /// <summary>Function summary 2.</summary>  
        /// <param name="a" type="String">A string.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        return a;  
    }  
    ```  
  
2.  XML ドキュメントのコメントを表示するには、名前には、次の例のように、XML ドキュメントのコメントが付いている関数のかっこを入力します。  
  
    ```javascript  
    calc(  
    ```  
  
### ローカライズされた IntelliSense を作成するのには  
  
1.  OpenAjax MessageBundle フォーマットでは、ドキュメント コメントを XML ファイルを作成します。  
  
    > [!IMPORTANT]
    >  MessageBundle は、推奨される形式です。  この形式では、Microsoft Ajax または .winmd ファイルではサポートされていません。  もう 1 つを使用しての詳細については`VSDoc`フォーマットは、 [\<loc\>](../ide/loc-javascript.md)。  
  
     次の使用例サイドカーファイル ファイルで IntelliSense のローカライズされた情報を含むコンテンツが表示されます。  これは、JA など、カルチャに固有のフォルダー内にある XML ファイルです。  フォルダーを含む .js ファイルと同じ場所にする必要があります、 `<loc>`要素。  XML ファイルのファイル名と一致する必要があります、 `filename`で指定されたパラメーター、 `<loc>`要素。  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  .Js ファイルでは、次のコードを追加します。  `<loc>`要素は、スクリプトの前に宣言する必要あるし、としての同じ使用規則に依存して、 `<reference>`要素。  詳細については、「[JavaScript IntelliSense](../ide/javascript-intellisense.md)」および「[\<loc\>](../ide/loc-javascript.md)」を参照してください。  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  .Js ファイルでは、XML ドキュメントの要素および既定の説明を追加します。  設定、 `locid`属性の値が対応する一致する`name`サイドカーファイル ファイルから属性の値。  可能な場合、ローカライズされた IntelliSense については、既定の説明に変わります。  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  XML ドキュメントのコメントを表示するには、名前と、次の例のように、関数のかっこを入力します。  
  
    ```javascript  
    add(  
    ```  
  
## 参照  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Walkthrough: JavaScript IntelliSense in ASP.NET](http://msdn.microsoft.com/ja-jp/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)