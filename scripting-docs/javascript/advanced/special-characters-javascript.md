---
title: 特殊文字 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- line terminator character
- white space character
- Unicode character
- escape sequence
- backslash (\)
ms.assetid: 3b38b1bd-1f0f-4748-b13e-55cab36fd126
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0eaae8dfc84d9a3be6db54c50558d4cf675a53a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569632"
---
# <a name="special-characters-javascript"></a>特殊文字 (JavaScript)
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] にはエスケープ シーケンスが用意されており、直接入力できない文字を文字列として使用できます。  
  
## <a name="remarks"></a>コメント  
 文字列値は、0 個以上の Unicode 文字 (英字、数字、およびその他の文字) の連続です。 文字列リテラルは単一引用符または二重引用符で囲まれています。 二重引用符は、単一引用符で囲まれた文字列に含めることができます。 単一引用符は、二重引用符で囲まれた文字列に含めることができます。  
  
 文字列リテラルの各文字は、エスケープ シーケンスによって表すことができます。 エスケープ シーケンスは、次に続く文字が特殊文字であることを [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のインタープリターに知らせる円記号 (\\) で始まります。  
  
 \u*hhhh* エスケープ シーケンスを使用して Unicode 文字を指定することができます。ここで、*hhhh* は 4 桁の 16 進数です。 Unicode エスケープ シーケンスは 16 ビットの文字を表すことができます。 詳細については、「[Unicode コード ポイントのエスケープ シーケンス](#CodePoint)」を参照してください。  
  
 一部の文字には単一文字のエスケープ シーケンスを使用できます。 たとえば、\t はタブ文字を指定します。  
  
## <a name="escape-sequences"></a>エスケープ シーケンス  
 次の表では、一般的な文字のエスケープ シーケンスの例をいくつか示します。  
  
|Unicode 文字の値です。|エスケープ シーケンス|説明|カテゴリ|  
|-----------------------------|---------------------|-------------|--------------|  
|\u0008|\b|バックスペース||  
|\u0009|\t|タブ|空白|  
|\u000A|\n|ライン フィード (改行)|行終端記号|  
|\u000B|\v<br /><br /> (この表の後の注意を参照してください。)|垂直タブ|空白|  
|\u000C|\f|フォーム フィード|空白|  
|\u000D|\r|キャリッジ リターン|行終端記号|  
|\u0020||スペース|空白|  
|\u0022|\\"|二重引用符 (")||  
|\u0027|\\'|単一引用符 (')||  
|\u005C|\\\|円記号 (\\)||  
|\u00A0||非区切りスペース|空白|  
|\u2028||行区切り|行終端記号|  
|\u2029||段落区切り|行終端記号|  
|\uFEFF||バイト順マーク (BOM: Byte Order Mark)|空白|  
  
 カテゴリ列は、文字が空白または行終端記号の文字であるかどうかを示します。 [trim メソッド (文字列)](../../javascript/reference/trim-method-string-javascript.md) は、文字列から先頭および末尾の空白と行終端記号の文字を削除します。  
  
 円記号 (\) 自体はエスケープ文字として使用されます。 したがって、スクリプトに直接入力することはできません。 円記号を記述する場合は、円記号を 2 つ続けて (\\\\) 入力する必要があります。  
  
> [!NOTE]
>  [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 以降、垂直タブ (\v) と "v" の等価性テストによってブラウザーを Internet Explorer と識別することができなくなりました。 旧バージョンでは、式 `"\v" === "v"` は `true` を返します。 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] では、式は `false` を返します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 エスケープ シーケンス \\\ および \\' の使用例を次に示します。  
  
### <a name="code"></a>コード  
  
```JavaScript  
document.write('The image path is C:\\webstuff\\mypage\\gifs\\garden.gif.');  
document.write ("<br />");  
document.write('The caption reads, "After the snow of \'97. Grandma\'s house is covered."');  
```  
  
<a name="CodePoint"></a>   
## <a name="unicode-code-point-escape-sequences"></a>Unicode コード ポイントのエスケープ シーケンス  
 [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)] では、Unicode が完全にサポートされています。 最も一般的な Unicode コード ポイントは、タブ文字を示す /u0009 のように、4 つの 16 進数で表されます。 5 つ以上の 16 進数字が必要なシンボルをすべて含む、アストラル コード ポイントは、簡略化された形式でサポートされるようになりました。 "\u{*codepoint*}" 形式を使用すると、完全な Unicode 文字セットをリテラル形式で表現できます。 たとえば、「𠮷」記号を表すには、"\u{20BB7}" 形式を使用できます。  
  
 次のコード例で、文字列はすべて同等です。 (\uD842\uDFB7 は、以前のバージョンでこのシンボルを指定するための代替方式です)。  
  
```JavaScript  
"\u{20BB7}"=="𠮷"=="\uD842\uDFB7"  
```  
  
 RegExp には、アストラル コード ポイントの完全なサポートを有効にするための、/u フラグが含まれるようになりました。 たとえば、次のコード例では、正規表現内の /u フラグによって、アストラル コード ポイントとのマッチングが可能になります (ピリオドは指定された文字列内の任意の文字と一致します)。  
  
```JavaScript  
"𠮷".match(/./u)[0].length == 2  
```  
  
 /u フラグによって、新しい形式 \u{codepoint}) を Unicode エスケープ シーケンスとして解析できます。 これが必要となるのは、/u フラグのない \u{xxxxx} が、正規表現で異なる意味になるためです。  
  
> [!NOTE]
>  アストラル コード ポイントでは、長さは常に 2 です。 これは以前のバージョンでの動作と一致します。  
  
 String オブジェクトには、アストラル コード ポイントをサポートする 2 つの新しいメソッド、String.codePointAt および String.fromCodePoint が含まれるようになりました。 たとえば、codePointAt を使用して、「𠮷」シンボルと同等のコード ポイントを返すことができます。  
  
```JavaScript  
"𠮷".codePointAt(0) == 0x20BB7  
  
```  
  
 また、`for...of` ステートメントを使用して、コード ポイントを反復することもできます。  
  
```JavaScript  
for(var c of "𠮷") {  
    console.log(c);  
}  
  
```  
  
## <a name="see-also"></a>関連項目  
 [String.fromCharCode 関数](../../javascript/reference/string-fromcharcode-function-javascript.md)