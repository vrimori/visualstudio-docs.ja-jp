---
title: "JScript スクリプトのトラブルシューティング (JavaScript) | Microsoft Docs"
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
- automative type conversion
- troubleshooting scripts
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e0193e6dc0996d5e2d0d3df7103c7705d29477
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-your-scripts-javascript"></a>JScript スクリプトのトラブルシューティング (JavaScript)
どのようなプログラミング言語でも、思いがけない動きをする部分があります。 たとえば、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の `null` 値は、C 言語または C++ 言語の `Null` 値と動作が異なります。  
  
 ここでは、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] スクリプトを記述するときに発生する可能性のある問題をいくつか紹介します。  
  
## <a name="syntax-errors"></a>構文エラー  
 スクリプトを記述するときは細心の注意を払う必要があります。 たとえば、文字列は引用符で囲む必要があります。  
  
## <a name="order-of-script-interpretation"></a>スクリプトの解釈の順序  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の解釈は、Web ブラウザーの HTML 解析プロセスの一部として行われます。 ドキュメントの \<HEAD> のタグ内にスクリプトを配置すると、\<BODY> タグのどの部分よりも先に解釈されます。 \<BODY> タグで作成されるオブジェクトは、\<HEAD> を解析する時点では存在しないので、それをスクリプトで操作することはできません。  
  
> [!NOTE]
>  これは Internet Explorer 固有の動作です。 ASP および WSH には、(他のホストと同様に) 異なる実行モデルがあります。  
  
## <a name="automatic-type-coercion"></a>自動強制型変換  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は、自動強制型変換が行われる、型指定の緩い言語です。 異なる型を持つ値どうしは等しくないにもかかわらず、次に示す式の例は **true** として評価されます。  
  
```JavaScript  
"100" == 100;  
false == 0;  
```  
  
 型と値の両方が同じであることを確認するには、厳密等価演算子 (===) を使います。 次の例は、どちらも false に評価されます。  
  
```JavaScript  
"100" === 100;  
false === 0;  
```  
  
## <a name="operator-precedence"></a>演算子の優先順位  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)によって、式の評価中に演算子が実行されるタイミングが決まります。 次の式では、減算演算子の方が前にありますが、乗算が先に実行されます。  
  
```JavaScript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## <a name="using-forin-loops-with-objects"></a>オブジェクトでの for...in ループの使用  
 オブジェクトの各プロパティに対して [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) ループで反復処理する場合、オブジェクトの各フィールドがループ カウンター変数に代入される順序を予測または制御することはできません。 さらに、言語の実装が異なると、この順序も異なる可能性があります。  
  
## <a name="with-keyword"></a>with キーワード  
 [with](../../javascript/reference/with-statement-javascript.md) ステートメントは、指定したオブジェクトに既に存在するプロパティにアクセスする場合には便利ですが、オブジェクトへのプロパティの追加に使うことはできません。 オブジェクト内に新しいプロパティを作成するには、オブジェクトを明示的に参照する必要があります。  
  
## <a name="this-keyword"></a>this キーワード  
 オブジェクトの定義内に存在する `this` キーワードを使ってそのオブジェクト自体を参照することはできますが、現在実行中の関数がオブジェクト定義ではない場合は、`this` キーワードやその他の類似したキーワードを使って、その関数を参照することはできません。 その関数がメソッドとしてオブジェクトに割り当てられる場合は、関数内で `this` キーワードを使って、そのオブジェクトを参照できます。  
  
## <a name="writing-a-script-that-writes-a-script-in-internet-explorer"></a>Internet Explorer でスクリプトを出力するスクリプトの作成  
 \</SCRIPT> タグは、インタープリターで解釈されると、現在のスクリプトを終了します。 "\</SCRIPT>" 自体を表示するには、少なくとも 2 つの文字列として書き直してください。たとえば、"\</SCR" と "IPT>" のように記述すると、それらを表示するステートメントの中で 2 つを連結できます。  
  
## <a name="implicit-window-references-in-internet-explorer"></a>Internet Explorer での暗黙のウィンドウ参照  
 複数のウィンドウを同時に開くことができるため、暗黙のウィンドウ参照はすべて、現在のウィンドウを指します。 他のウィンドウを指すには、明示的な参照を使う必要があります。