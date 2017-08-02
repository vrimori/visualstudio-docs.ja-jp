---
title: "識別子の入力候補 | Microsoft Docs"
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
  - "IntelliSense [JavaScript], ステートメント入力候補"
  - "ステートメント入力候補, JavaScript IntelliSense"
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 識別子の入力候補
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript の変数の宣言を入力明示的に許可されていません。  したがって、IntelliSense はオブジェクトの入力候補リストは、常に提供できません。  さまざまな状況で発生します。  いくつかの一般的なものを次に示します。  
  
-   パラメーターが宣言されているが、他の場所で作業中の文書には、次の例に示すように呼び出されていません。  
  
    ```javascript  
    function illuminate(light) {  
             light.  // Accurate statement completion is not available   
                     // unless illuminate is called elsewhere with a   
                     // parameter that has a value. If it is called only  
                     // in a function that is a sibling to   
                     // illuminate(light) in the call hierarchy, the   
                     // IntelliSense engine also cannot determine the   
                     // parameter type.  
         }  
  
    // Sibling function. No statement completion for light   
    // object in preceding code.  
    function lightLamp() {  
        var x = illuminate(1);  
    }  
  
    // Uncomment the next line to obtain statement completion for  
    // light object in preceding code.  
    // var x = illuminate(1);  
    ```  
  
-   オブジェクトは、イベントに応答して呼び出される関数です。  デザイン時に、IntelliSense エンジンはこのような状況で使用されるオブジェクトの種類を判断できません。  
  
     IntelliSense エンジン イベント、通常の使用によって呼び出されることを確認することができる場合は、 `addEventListener`のイベントでは、作業中の文書、IntelliSense のより正確な情報が提供されます。  
  
 IntelliSense、オブジェクトを識別できない場合は、IntelliSense エンジン名前付きエンティティ、または、作業中の文書が存在する識別子、コンプリート リストが表示されます。  コンプリート リストにはこれらの識別子が含まれている場合は、それらの横に情報アイコンが表示されます。  また、各識別子のツールヒントに式が不明であることを示します。  次の図は、補完オプションの種類のオブジェクトのステートメントが表示されます`light`は見つかりませんでした、オブジェクトとそのプロパティが定義されているため。  ただし、 `intensity`で使用されているためプロパティは、\[識別子\] ボックスの一覧で使用可能な`illuminate`関数。  
  
 **補完オプションを識別することはできません、オブジェクト**  
  
 ![識別子の JavaScript IntelliSense](~/ide/media/js_intellisense_identifiers.png "js\_intellisense\_identifiers")  
  
 XML ドキュメントのコメントや JavaScript の IntelliSense 拡張機能を使用して、オブジェクトの候補の一覧をオーバーライドできます。  それ以外の場合利用できることがあるとこれらの機能を使用するから型情報と IntelliSense のより詳細な情報入手できます。  詳細については、「[JavaScript IntelliSense の拡張](../ide/extending-javascript-intellisense.md)」および「[方法: JavaScript XML ドキュメントのコメントを作成する](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)」を参照してください。  
  
## 参照  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)