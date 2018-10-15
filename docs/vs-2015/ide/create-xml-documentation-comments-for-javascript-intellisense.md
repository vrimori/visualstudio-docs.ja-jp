---
title: JavaScript IntelliSense の XML ドキュメントのコメントを作成する |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d15144a2cee70e5f6bdc496bf2c09eb8fb95c85d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220559"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>JavaScript IntelliSense の XML ドキュメントのコメントを作成します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*XML ドキュメント コメント*JavaScript コメント関数、フィールド、および変数などのコード要素に関する情報を提供するスクリプトに追加することができます。 Visual Studio で、これらの説明テキストがスクリプト関数を参照するときに IntelliSense に表示されます。  
  
 このトピックでは、XML ドキュメント コメントの使用に関する基本的なチュートリアルを提供します。 については、他の要素を使用して[ \<var >](../ide/var-javascript.md)と[\<値 >](../ide/value-javascript.md)、および追加のコード例については、次を参照してください[XML ドキュメントのコメント。](../ide/xml-documentation-comments-javascript.md). など、非同期コールバックの IntelliSense の情報を提供する方法については、`Promise`を参照してください[\<返します >](../ide/returns-javascript.md)します。  
  
> [!NOTE]
>  XML ドキュメントのコメントは、参照されるファイル、アセンブリ、およびサービスでのみ使用できます。  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>JavaScript 関数の XML ドキュメント コメントを作成するには  
  
-   関数で追加[\<概要 >](../ide/summary-javascript.md)、 [ \<param >](../ide/param-javascript.md)と[\<を返します >](../ide/returns-javascript.md)要素の各要素の前に、3 つのスラッシュ記号 (///) です。  
  
    > [!NOTE]
    >  各要素は、1 行にある必要があります。  
  
     次の例では、JavaScript 関数を示します。  
  
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
  
-   XML ドキュメント コメントを表示するには、名前と次の例のように、XML ドキュメント コメントでマークされている関数の始めかっこを入力します。  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     XML ドキュメント コメントを含む関数の始めかっこを入力すると、コード エディターは IntelliSense を使用して、XML ドキュメント コメントで定義されている情報を表示します。  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>JavaScript のフィールドの XML ドキュメントのコメントを作成するには  
  
-   コンス トラクター関数またはオブジェクト定義、追加、 [\<フィールド >](../ide/field-javascript.md)要素に続く 3 つのスラッシュ (///)。  
  
     次の例では、使用、`<field>`コンス トラクター関数内の要素。 その他の例では、次を参照してください。 [\<フィールド >](../ide/field-javascript.md)します。  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   XML ドキュメント コメントを表示するには、次の例のように、XML ドキュメントのコメントをマークされている関数コンス トラクターを使用してオブジェクトを作成します。  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   次の行には、オブジェクトと、フィールドの IntelliSense 情報を表示する期間の名前を入力します。  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>オーバー ロードされた関数の場合、XML ドキュメント コメントを作成するには  
  
1.  関数では、追加、 [\<署名 >](../ide/signature-javascript.md)各オーバー ロードの要素。 これらの要素で、追加など、他の要素`<summary>`、 `<param>`、および`<returns>`、3 つのスラッシュ (///) を持つ各要素の前します。  
  
     次の例では、オーバー ロードの JavaScript 関数を示します。 この例では、オーバー ロードは、パラメーターの型によって異なります。  
  
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
  
2.  XML ドキュメント コメントを表示するには、名前と次の例のように、XML ドキュメント コメントでマークされている関数の始めかっこを入力します。  
  
    ```javascript  
    calc(  
    ```  
  
### <a name="to-create-localized-intellisense"></a>ローカライズされた IntelliSense を作成するには  
  
1.  OpenAjax MessageBundle 形式でドキュメントのコメントを含む XML ファイルを作成します。  
  
    > [!IMPORTANT]
    >  MessageBundle は、推奨される形式です。 Microsoft Ajax または .winmd ファイルは、この形式はサポートされていません。 代わりに、使用について`VSDoc`書式設定を参照してください[ \<loc >](../ide/loc-javascript.md)します。  
  
     次の例を示しています、ローカライズされた IntelliSense 情報を含むサイドカー ファイルのコンテンツ。 これは、JA など、カルチャ固有のフォルダーにある XML ファイルです。 フォルダーを格納する .js ファイルと同じ場所にある必要があります、`<loc>`要素。 XML ファイルのファイル名に一致する必要があります、`filename`パラメーターで指定された、`<loc>`要素。  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  .Js ファイルには、次のコードを追加します。 `<loc>`要素は、任意のスクリプトでは、前に宣言する必要がありますと同じ使用状況規則に従います、`<reference>`要素。 詳細については、次を参照してください。 [JavaScript IntelliSense](../ide/javascript-intellisense.md)と[ \<loc >](../ide/loc-javascript.md)します。  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  .Js ファイルには、XML ドキュメントの要素とその既定の説明を追加します。 設定、`locid`属性値に対応する一致`name`サイドカー ファイルからの属性値。 使用できる場合、ローカライズされた IntelliSense 情報が既定の説明が置き換えられます。  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  XML ドキュメント コメントを表示するには、名前と次の例のように、関数の始めかっこを入力します。  
  
    ```javascript  
    add(  
    ```  
  
## <a name="see-also"></a>関連項目  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [XML ドキュメント コメント](../ide/xml-documentation-comments-javascript.md)   
 [NIB: チュートリアル: ASP.NET での JavaScript IntelliSense](http://msdn.microsoft.com/en-us/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)



