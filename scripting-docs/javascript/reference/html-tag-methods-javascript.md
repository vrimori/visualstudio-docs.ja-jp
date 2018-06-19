---
title: HTML Tag メソッド (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- link method [JavaScript]
- blink method [JavaScript]
- fontsize method [JavaScript]
- italics method [JavaScript]
- sup method [JavaScript]
- anchor method [JavaScript]
- fixed method [JavaScript]
- fontcolor method [JavaScript]
- bold method [JavaScript]
- small method [JavaScript]
- HTML Tag methods [JavaScript]
- sub method [JavaScript]
- big method [JavaScript]
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7639bc609d8e9b7e4b212fe67ae40f81487d708e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638652"
---
# <a name="html-tag-methods-javascript"></a>HTML タグ メソッド (JavaScript)
テキストを HTML 要素を配置する HTML タグ メソッドを使用することができます、`String`オブジェクト。  
  
## <a name="syntax"></a>構文  
 次の表は、構文と、各 HTML タグ メソッドの説明を示します。  
  
 [構文] 列で`string1`は、`String`オブジェクトまたはリテラルです。  
  
 標準の列を示します[World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?LinkId=199553) HTML 4 に関する推奨事項です。 「推奨」は、スタイル シートを優先するため、HTML 要素が推奨されないことを示します。  
  
|構文|メソッドの説明|パラメーターの説明|標準|  
|------------|------------------------|---------------------------|--------------|  
|`string1`.anchor (`name`)|テキストを囲む名前属性を含む HTML アンカーを配置します。|`name`パラメーターは、HTML アンカーの NAME 属性に格納するテキスト。||  
|`string1`.big()|HTML の配置\<BIG >、テキスト タグで囲みます。||推奨しません|  
|`string1`.blink()|HTML の配置\<BLINK >、テキスト タグで囲みます。 \<BLINK > タグが Internet Explorer でサポートされていません。||標準ではなく|  
|`string1`.bold()|HTML の配置\<B >、テキスト タグで囲みます。||推奨しません|  
|`string1`.fixed()|HTML の配置\<TT >、テキスト タグで囲みます。||推奨しません|  
|`string1`.fontcolor (`color`)|HTML の配置\<フォント > テキストの周辺の色の属性を持つタグ。|`color`パラメーターは、16 進値または色の定義済みの名前を含む文字列値です。 有効な定義済みの色の名前が異なります、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]ブラウザーとそのバージョンをホストします。|非推奨|  
|`string1`.fontsize (`size`)|HTML の配置\<フォント > テキストの周辺の SIZE 属性を持つタグ。|`size`パラメーターは、テキストのサイズを指定する整数値。 有効な整数値によって異なります、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]ブラウザーとそのバージョンをホストします。|非推奨|  
|`string1`.italics()|HTML の配置\<I >、テキスト タグで囲みます。||推奨しません|  
|`string1`ある .link (`href`)|テキストを HREF 属性を持つ HTML アンカーを配置します。|`href`パラメーターは、HTML アンカーの HREF 属性に格納するテキスト。||  
|`string1`.small()|HTML の配置\<小さな >、テキスト タグで囲みます。||推奨しません|  
|`string1`.strike()|HTML の配置\<STRIKE >、テキスト タグで囲みます。||非推奨|  
|`string1`.sub()|HTML の配置\<SUB >、テキスト タグで囲みます。|||  
|`string1`.sup()|HTML の配置\<SUP >、テキスト タグで囲みます。|||  
  
## <a name="remarks"></a>コメント  
 文字列を HTML タグが適用されて既にかどうかを決定するチェックは行われません。  
  
## <a name="example"></a>例  
 次の例では、HTML タグ メソッドを使用する方法を示します。  
  
```JavaScript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)