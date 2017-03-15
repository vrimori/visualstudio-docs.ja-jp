---
title: JavaScript IntelliSense | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
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
author: mikejo
ms.author: mikejo
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
translationtype: Human Translation
ms.sourcegitcommit: d07820eda0d76163d99d7752789750eaf56182fd
ms.openlocfilehash: 1f8372fe201d6b23ee2c65e0f6d6a2fa28976654
ms.lasthandoff: 02/22/2017

---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] では、すぐに使用できる強力な JavaScript 編集エクスペリエンスが提供されます。 TypeScript ベースの言語サービスを活用して、Visual Studio で高度な IntelliSense が提供されます。また、最新の JavaScript 機能がサポートされ、定義へ移動、リファクタリングなどの生産性向上機能が改善されています。

> [!NOTE]
>  [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] の JavaScript 言語サービスでは、言語サービス ("salsa") の新しいエンジンが使用されます。 このトピックでも詳しく説明しますが、この[ブログ投稿](https://blogs.msdn.microsoft.com/visualstudio/2016/04/08/previewing-salsa-javascript-language-service-visual-studio-15/)も参照してください。 新しい編集機能はほとんど VS コードにも適用されます。 詳細については、[VS コードのドキュメント](https://code.visualstudio.com/docs/languages/javascript)を参照してください。

[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] の一般的な IntelliSense の機能の詳細については、「[IntelliSense の使用方法](../ide/using-intellisense.md)」を参照してください。 

## <a name="whats-new-in-the-javascript-language-service-in-includevsdev15miscincludesvsdev15mdmd"></a>[!include[vs_dev15](../misc/includes/vs_dev15_md.md)] の JavaScript 言語サービスの新機能

- 高度な IntelliSense

    [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] の JavaScript IntelliSense では、パラメーターおよびメンバー リストにさらに多くの情報が表示されるようになります。
この新しい情報は TypeScript 言語サービスで提供されます。この言語サービスでは、コードをよりよく理解するためにバックグラウンドで静的分析が使用されます。
TypeScript では、この情報を作成するためにいくつかのソースを使用します。
    - [型推論に基づく IntelliSense](#TypeInference)
    - [JSDoc に基づく IntelliSense](#JsDoc)
    - [TypeScript 宣言ファイルに基づく IntelliSense](#TSDeclFiles)

- [型定義の自動取得](#Auto)
- [ES6 以降のサポート](#ES6)
- [JSX 構文のサポート](#JSX)

## <a name="TypeInference"></a>型推論に基づく IntelliSense
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

## <a name="JsDoc"></a> JSDoc に基づく IntelliSense

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

## <a name="TsDeclFiles"></a> TypeScript 宣言ファイルに基づく IntelliSense

現在、JavaScript と TypeScript は同じ言語サービスに基づいているため、より多くの方法で対話することができます。 たとえば、JavaScript IntelliSense は、`.d.ts` ファイルで宣言された値に提供することができ ([詳細については、こちらを参照してください](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Writing%20Definition%20Files.md))、TypeScript で宣言されているインターフェイスやクラスなどの型は、JsDoc コメントの型として使用できます。 

(インターフェイス経由で) このような型情報を、(JsDoc タグを使用して) 同じプロジェクトの JavaScript ファイルに提供する TypeScript 定義ファイルの簡単な例を以下に示します。

_**JavaScript で使用されている TypeScript 宣言**_

<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/decl1.png" height="400" width="640"/>

## <a name="Auto"></a> 型定義の自動取得
TypeScript の世界では、最も一般的な JavaScript ライブラリに `.d.ts` ファイルで記述された API が含まれ、その定義で最も一般的なレポジトリは [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) にあります。

既定では、Salsa 言語サービスは使用されている JavaScript ライブラリを検出し、高度な IntelliSense を提供するためにライブラリを記述する、対応する `.d.ts` ファイルを自動的にダウンロードして参照しようとします。 ファイルは、`%LOCALAPPDATA%\Microsoft\TypeScript` のユーザー フォルダーの下にあるキャッシュにダウンロードされます。 

> [!NOTE]
> `tsconfig.json` 構成ファイルを使用する場合、この機能は既定で**無効**になりますが、有効に設定することができます (下記参照)。

現在、自動検出は npm (`package.json` ファイルを読み取る場合)、Bower (`bower.json` ファイルを読み取る場合) からダウンロードされる依存関係に対して機能します。また、おおよそ上位 400 の最も一般的な JavaScript ライブラリのリストに一致する、プロジェクトのルーズ ファイルにも有効です。 たとえば、プロジェクトに `jquery-1.10.min.js` がある場合、ファイル `jquery.d.ts` は、優れた編集エクスペリエンスを提供するためにフェッチされ、読み込まれます。 この `.d.ts` ファイルはプロジェクトには影響しません。 

自動取得を使用しない場合は、以下に示すとおり、構成ファイルを追加して無効にします。 プロジェクト内で直接使用する場合も定義ファイルを手動で配置できます。

## <a name="ES6"></a> ES6 以降のサポート

ES6 (ECMAScript 2015) は、JavaScript の次のバージョンです。 クラス、アロー関数、`let`/`const` などの新しい構文を言語に導入します。 この新しい構文はすべて Visual Studio でサポートされます。

TypeScript で提供される主要なフィーチャーの&1; つは、ES6 機能を使用して、コードを出力できることです。このコードは、新しい機能をまだ理解していない JavaScript ランタイムで実行できます。 これは、一般に "トランスパイラ" として知られています。 JavaScript では同じ言語サービスを使用するため、ES6 以降から ES5 へのトランスパイラも利用できます。

これを設定するには、構成オプションについてある程度理解する必要があります。  TypeScript は `tsconfig.json` ファイルを使用して構成します。 このようなファイルがない場合は、一部の既定値が使用されます。 互換性の理由から、JavaScript ファイル (および必要に応じて `.d.ts` ファイル) のみが存在する場合、これらの既定値は異なります。 JavaScript ファイルをコンパイルするには、`tsconfig.json` ファイルを追加する必要があり、これらの既定値の一部を明示的に設定する必要があります。

tsconfig ファイルに必要な設定について、以下に簡単に説明します。

 - `allowJs`: この値は、JavaScript ファイルが認識されるように `true` に設定する必要があります。
TypeScript は JavaScript にコンパイルするため、これは既定で `false` になります。これは、コンパイラでコンパイルされたファイルがインクルードされないようにするために必要です。
 - `outDir`: これは、出力された JavaScript ファイルが検出されず、プロジェクトに追加されるように、プロジェクトに含まれない場所に設定する必要があります (下記 `exclude` を参照)。
 - `module`: モジュールを使用する場合、この設定で、出力コードで使用する必要があるモジュール形式 (たとえば、Node、または Browserify などのバンドラーの場合は `commonjs`) をコンパイラに指示します。
 - `exclude`: この設定は、プロジェクトに含めないフォルダーを示しています。 
 出力場所と、`node_modules` や `temp` などのプロジェクト以外のフォルダーをこの設定に追加する必要があります。
 - `enableAutoDiscovery`: この設定は、前述のとおり、定義ファイルの自動検出とダウンロードを可能にします。
 - `compileOnSave`: この設定で、Visual Studio にソース ファイルが保存されるたびに再コンパイルする必要があるかどうかをコンパイラに指示します。

`./out` フォルダーで JavaScript ファイルを CommonJS モジュールに変換する場合、以下のような設定を `tsconfig.json` ファイルに含めることができます。

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "allowJs": true,
    "outDir": "out"
  },
  "exclude": [
    "node_modules",
    "wwwroot",
    "out"
  ],
  "compileOnSave": true,
  "typingOptions": {
    "enableAutoDiscovery": true
  }
}
```

上記のように設定した状態で、ECMAScript 2015 言語機能をいくつか含むソース ファイル (`./app.js`) が存在する場合は次のようになります。

```js
import {Subscription} from 'rxjs/Subscription';

class Foo {
    sayHi(name) {
        return `Hi ${name}, welcome to Salsa!`;
    }
}

export let sqr = x => x * x;
export default Subscription;
```

この場合、ファイルは次のような ECMAScript 5 (既定) を対象とする `./out/app.js` に出力されます。

```js
"use strict";
var Subscription_1 = require('rxjs/Subscription');
var Foo = (function () {
    function Foo() {
    }
    Foo.prototype.sayHi = function (name) {
        return "Hi " + name + ", welcome to Salsa!";
    };
    return Foo;
}());
exports.sqr = function (x) { return x * x; };
Object.defineProperty(exports, "__esModule", { value: true });
exports.default = Subscription_1.Subscription;
//# sourceMappingURL=app.js.map
```

## <a name="JSX"></a> JSX 構文のサポート

Visual Studio 2017 の JavaScript では、JSX 構文の豊富なサポートが提供されます。 JSX は、JavaScript ファイル内で HTML タグを許可する構文セットです。 

次の図は `comps.tsx` TypeScript ファイルに定義されている React コンポーネントを示しています。`app.jsx` ファイルから使用されるこのコンポーネントには、JSX 式に入力し、文書化するために IntelliSense が備わっています。
この具体例にはたまたま TypeScript コードも含まれていますが、TypeScript は必要ありません。
<img src="https://raw.githubusercontent.com/wiki/Microsoft/TypeScript/images/react.png" height="500" width="640"/>

> [!NOTE]
> JSX 構文を React 呼び出しに変換するには、設定 `"jsx": "react"` を、上記のとおり、`tsconfig.json` ファイルの `compilerOptions` に追加する必要があります。

ビルド時に './out/app.js' で作成された JavaScript ファイルには次のようなコードが含まれます。

```js
"use strict";
var comps_1 = require('./comps');
var x = React.createElement(comps_1.RepoDisplay, {description: "test"});
```

