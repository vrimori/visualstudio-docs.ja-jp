---
title: "JScript スクリプトのトラブルシューティング (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "自動的な型変換"
  - "トラブルシューティング (スクリプト)"
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# JScript スクリプトのトラブルシューティング (JavaScript)
どのようなプログラミング言語でも、思いがけない動きをする部分があります。  たとえば、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の `null` 値は、C 言語または C\+\+ の `Null` 値と動作が異なります。  
  
 ここでは、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] スクリプトを記述するときに発生する可能性のある問題をいくつか紹介します。  
  
## 構文エラー  
 スクリプトを記述するときには細心の注意を払う必要があります。  たとえば、文字列は引用符で囲む必要があります。  
  
## スクリプトの解釈の順序  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の解釈は、Web ブラウザーの HTML 解析プロセスの一部として行われます。  ドキュメントの \<HEAD\> のタグ内にスクリプトを記述すると、\<BODY\> タグのどの部分よりも先に解釈されます。  \<BODY\> タグで作成されるオブジェクトは、\<HEAD\> を解析する時点では存在しないので、それをスクリプトで操作することはできません。  
  
> [!NOTE]
>  この動作は Internet Explorer 固有の動作です。  ASP および WSH には、\(他のホストと同様に\) 異なる実行モデルがあります。  
  
## 自動強制型変換  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は、自動強制型変換が行われる、型指定の緩い言語です。  異なる型を持つ値どうしは等しくないにもかかわらず、次に示す式の例は **true** として評価されます。  
  
```javascript  
"100" == 100;  
false == 0;  
```  
  
 型と値の両方が同じであることを確認するには、厳密等価演算子 \(\=\=\=\) を使用します。  次の例は、どちらも false に評価されます。  
  
```javascript  
"100" === 100;  
false === 0;  
```  
  
## 演算子の優先順位  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)によって、式の評価中に演算子が実行されるタイミングが決まります。  次の式では、減算演算子の方が前にありますが、乗算が先に実行されます。  
  
```javascript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## オブジェクトでの for...in ループの使用  
 オブジェクトの各プロパティに対して [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) ループで反復処理する場合、オブジェクトの各フィールドがどのような順序でループ カウンター変数に代入されるかを予測または制御することはできません。  さらに、言語の実装が変われば、この順序も変わる可能性があります。  
  
## with キーワード  
 [with](../../javascript/reference/with-statement-javascript.md) ステートメントは、指定したオブジェクトに既に存在するプロパティにアクセスする場合には便利ですが、オブジェクトへのプロパティの追加に使用することはできません。  オブジェクト内に新しいプロパティを作成するには、オブジェクトを明示的に指定する必要があります。  
  
## this キーワード  
 `this` キーワードは、オブジェクトの定義内に存在してそのオブジェクト自体を参照しますが、現在実行中の関数がオブジェクト定義ではない場合は、`this` キーワードやその他の類似したキーワードを使用しても、その関数を参照することはできません。  その関数がメソッドとしてオブジェクトに割り当てられる場合は、関数内で `this` キーワードを使用してそのオブジェクトを参照できます。  
  
## Internet Explorer でスクリプトを出力するスクリプトの作成  
 \<\/SCRIPT\> タグがインタープリターで解釈されると、現在のスクリプトは終了します。  "\<\/SCRIPT\>" 自体を表示するには、少なくとも 2 つの文字列として書き直してください。たとえば、"\<\/SCR" と "IPT\>" のように記述すると、それらを表示するステートメントの中で 2 つを連結できます。  
  
## Internet Explorer での暗黙のウィンドウ参照  
 複数のウィンドウを同時に開くことができるため、暗黙のウィンドウ参照はすべて、現在のウィンドウを指します。  その他のウィンドウを指すには、明示的な参照を使用する必要があります。