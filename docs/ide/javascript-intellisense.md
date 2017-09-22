---
title: JavaScript IntelliSense | Microsoft Docs
ms.custom: 
ms.date: 06/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 759ffc281b8c673f5987afc6512b225434b69dec
ms.contentlocale: ja-jp
ms.lasthandoff: 07/11/2017

---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] では、すぐに使用できる強力な JavaScript 編集エクスペリエンスが提供されます。 TypeScript ベースの言語サービスを活用して、Visual Studio で高度な IntelliSense が提供されます。また、最新の JavaScript 機能がサポートされ、定義へ移動、リファクタリングなどの生産性向上機能が改善されています。

> [!NOTE]
>  [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] の JavaScript 言語サービスでは、言語サービス ("salsa") の新しいエンジンが使用されます。 このトピックでも詳しく説明しますが、この[ブログ投稿](https://blogs.msdn.microsoft.com/visualstudio/2016/11/28/more-productive-javascript-in-visual-studio-2017-rc)も参照してください。 新しい編集機能はほとんど VS コードにも適用されます。 詳細については、[VS コードのドキュメント](https://code.visualstudio.com/docs/languages/javascript)を参照してください。

[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] の一般的な IntelliSense の機能の詳細については、「[IntelliSense の使用方法](../ide/using-intellisense.md)」を参照してください。 

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] の JavaScript 言語サービスの新機能

[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] の JavaScript IntelliSense では、パラメーターおよびメンバー リストにさらに多くの情報が表示されるようになります。
この新しい情報は TypeScript 言語サービスで提供されます。この言語サービスでは、コードをよりよく理解するためにバックグラウンドで静的分析が使用されます。
TypeScript では、この情報を作成するためにいくつかのソースを使用します。
- [型推論に基づく IntelliSense](#TypeInference)
- [JSDoc に基づく IntelliSense](#JsDoc)
- [TypeScript 宣言ファイルに基づく IntelliSense](#TSDeclFiles)
- [型定義の自動取得](#Auto)

### <a name="TypeInference"></a>型推論に基づく IntelliSense
JavaScript では、ほとんどの場合、明示的な型情報を利用できません。 幸い、周囲のコード コンテキストから型を推測するのは実に簡単です。
このプロセスを型推論と呼びます。

変数またはプロパティの場合、一般的に初期化の際に使用される値の型、または最新の割り当て値の型となります。 

```js
var nextItem = 10;
nextItem; // here we know nextItem is a number

nextItem = "box";
nextItem; // now we know nextItem is a string
```

関数の場合、return ステートメントから戻り値を推測できます。 

関数パラメーターの場合、現時点では推測されませんが、JSDoc または TypeScript の `.d.ts` ファイル (以降のセクションを参照) を使用してこれに対処する方法があります。

さらに、次のような特殊な推論があります。
 - "ES3 形式" クラス。プロトタイプ プロパティへのコンストラクター関数と割り当てを使用して指定します。
 - CommonJS 形式のモジュールパターン。`exports` オブジェクトでのプロパティ割り当て、または `module.exports` プロパティへの割り当てとして指定します。

```js
function Foo(param1) {
    this.prop = param1;
}
Foo.prototype.getIt = function () { return this.prop; };
// Foo will appear as a class, and instances will have a 'prop' property and a 'getIt' method.

exports.Foo = Foo;
// This file will appear as an external module with a 'Foo' export.
// Note that assigning a value to "module.exports" is also supported.
```

### <a name="JsDoc"></a> JSDoc に基づく IntelliSense

型推論で必要な (またはドキュメントを補足するための) 型情報が提供されない場合、型情報は JSDoc 注釈で明示的に指定されることがあります。  たとえば、部分的に宣言されたオブジェクトに特定の型を指定する場合、次のように `@type` タグを使用できます。

```js
/**
 * @type {{a: boolean, b: boolean, c: number}}
 */
var x = {a: true};
x.b = false;
x. // <- "x" is shown as having properties a, b, and c of the types specified
```

前述のとおり、関数パラメーターが推測されることはありません。 ただし、JSDoc の `@param` タグを使用すれば、関数パラメーターにも型を追加することができます。 

```js
/**
 * @param {string} param1 - The first argument to this function
 */
function Foo(param1) {
    this.prop = param1; // "param1" (and thus "this.prop") are now of type "string".
}
```
 
現在サポートされている JsDoc 注釈については、[このドキュメント](https://github.com/Microsoft/TypeScript/wiki/JsDoc-support-in-JavaScript)を参照してください。

### <a name="TsDeclFiles"></a> TypeScript 宣言ファイルに基づく IntelliSense

現在、JavaScript と TypeScript は同じ言語サービスに基づいているため、より多くの方法で対話することができます。 たとえば、JavaScript IntelliSense は、`.d.ts` ファイルで宣言された値に提供することができ ([詳細については、こちらを参照してください](https://www.typescriptlang.org/docs/handbook/declaration-files/introduction.html))、TypeScript で宣言されているインターフェイスやクラスなどの型は、JsDoc コメントの型として使用できます。 

(インターフェイス経由で) このような型情報を、(JsDoc タグを使用して) 同じプロジェクトの JavaScript ファイルに提供する TypeScript 定義ファイルの簡単な例を以下に示します。

_**JavaScript で使用されている TypeScript 宣言**_

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

### <a name="Auto"></a> 型定義の自動取得
TypeScript の世界では、最も一般的な JavaScript ライブラリに `.d.ts` ファイルで記述された API が含まれ、その定義で最も一般的なレポジトリは [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) にあります。

既定では、Salsa 言語サービスは使用されている JavaScript ライブラリを検出し、高度な IntelliSense を提供するためにライブラリを記述する、対応する `.d.ts` ファイルを自動的にダウンロードして参照しようとします。 ファイルは、`%LOCALAPPDATA%\Microsoft\TypeScript` のユーザー フォルダーの下にあるキャッシュにダウンロードされます。 

> [!NOTE]
> `tsconfig.json` 構成ファイルを使用する場合、この機能は既定で**無効**になりますが、有効に設定することができます (下記参照)。

現在、自動検出は npm (`package.json` ファイルを読み取る場合)、Bower (`bower.json` ファイルを読み取る場合) からダウンロードされる依存関係に対して機能します。また、おおよそ上位 400 の最も一般的な JavaScript ライブラリのリストに一致する、プロジェクトのルーズ ファイルにも有効です。 たとえば、プロジェクトに `jquery-1.10.min.js` がある場合、ファイル `jquery.d.ts` は、優れた編集エクスペリエンスを提供するためにフェッチされ、読み込まれます。 この `.d.ts` ファイルはプロジェクトには影響しません。 

自動取得を使用しない場合は、以下に示すとおり、構成ファイルを追加して無効にします。 プロジェクト内で直接使用する場合も定義ファイルを手動で配置できます。



