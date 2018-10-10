---
title: RequireJS 用に IntelliSense をカスタマイズ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 04cffba0f7bd03cbb4fb2fe228174377871c35f8
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880670"
---
# <a name="customizing-intellisense-for-requirejs"></a>RequireJS 用に IntelliSense をカスタマイズする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Visual Studio 2017 ドキュメント](/visualstudio/)します。  
  
Visual Studio 2013 Update 4 以降では、人気のある RequireJS JavaScript ファイルとモジュール式ローダーがサポートされるようになりました。 RequireJS を使用すると、コード モジュール間の依存関係を定義し、必要な場合にのみモジュールを動的に読み込む処理が簡単になります。 RequireJS を使用する JavaScript コードを作成する際には、モジュール定義から参照するモジュールや、コード内から `require()` への呼び出しを使用して参照するモジュールに対して、IntelliSense による候補が提示されます。  
  
 既定では、Visual Studio は RequireJS に対してごく基本的な構成のみのサポートを提供しますが、一般的には独自のカスタム構成設定をセットアップする (つまり、ライブラリの別名を定義する) のが通例となっています。 このトピックでは、プロジェクトの独特のセットアップを処理するために Visual Studio をカスタマイズするさまざまな方法について説明します。  
  
 このトピックでは、次の方法を説明します。  
  
-   ASP.NET プロジェクトで RequireJS をカスタマイズする  
  
-   JSProj プロジェクトで RequireJS をカスタマイズして、Apache Cordova アプリ、Windows ストア アプリ、および LightSwitch HTML アプリを構築するために使用する  
  
## <a name="customize-requirejs-in-aspnet-projects"></a>ASP.NET プロジェクトで RequireJS をカスタマイズする  
 Require.js という名前のファイルが現在の JavaScript ファイルで参照されている場合に自動的に RequireJS のサポートが有効になって (詳細については、IntelliSense のコンテキスト確認」セクションを参照してください。 [JavaScript IntelliSense](../ide/javascript-intellisense.md))。 ASP.NET プロジェクトで require.js を参照するは、普通///を使用して\<参照/> ディレクティブ _references.js ファイル内で。  
  
### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>ASP.NET プロジェクトで data-main 属性を構成する  
 アプリを実行した時の動作を正確にシミュレートするには、require.js の設定時に最初に読み込まれるファイルを JavaScript エディターが認識する必要があります。 これは、通常、次に示すように require.js を参照する script 要素の `data-main` 属性を使用して、アプリケーションの HTML ファイル内で構成します。  
  
```html  
<script src="js/require.js" data-main="js/app.js"></script>  
```  
  
 この例では、data-main によって参照されるスクリプト (js/app.js) は、require.js の直後に読み込まれます。 直後に読み込まれるファイルは、まず、RequireJS を使用する最適な場所 (を使用して`require.config()`)。使用するには、どのようなファイルを JavaScript エディターに通知する`data-main`アプリケーションでは、追加、`data-main`属性、および変更し、///\<参照/> ディレクティブ、アプリケーション内で require.js を参照します。 たとえば、このディレクティブを使用することができます。  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" />  
```  
  
### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>ASP.NET プロジェクトでアプリケーションのスタート ページを構成する  
 アプリの実行時に requirejs は相対ファイルへのパス (たとえば、"..\\"パス) では、require.js ライブラリが読み込まれている HTML ファイルに対して相対的です。 Visual Studio エディターで ASP.NET プロジェクトのコードを記述するときは、この開始ページが不明であるため、相対ファイル パスに使用する開始ページをエディターに知らせる必要があります。 これを行うには、追加、`start-page`属性を///\<参照/> ディレクティブ。  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />  
```  
  
 `start-page` 属性には、アプリの実行時にブラウザーに表示されるページの URL を指定します。  
  
## <a name="customize-requirejs-in-jsproj-projects"></a>JSProj プロジェクトで RequireJS をカスタマイズする  
 JSProj プロジェクト (末尾に拡張子 .jsproj の付いたプロジェクト ファイル) は、Apache Cordova 用のアプリ、HTML ベースの Windows ストア アプリ、または LightSwitch HTML アプリをビルドするときに使用します。 ASP.NET のプロジェクトとは異なり、これらのプロジェクトは、プロジェクト内に存在する HTML ファイルから .js ファイルへの参照を読み取ります。 このため、JSProj プロジェクト内の JavaScript ファイルを編集する際に、require.js を参照する別の HTML ファイルで現在編集中の JavaScript ファイルが参照されている場合に、RequireJS のサポートが有効になっているのを見ることができます。  
  
 JSProj プロジェクト ファイルでは、ASP.NET プロジェクトに必要なカスタマイズの手順は必要ありません。 つまり、require.js を参照する script タグの `data-main` 属性で使用されているスクリプト ファイルが自動的に読み込まれて require.js が構成されます。 require.js を参照する、HTML ファイルは、アプリケーションのスタート ページとしても使用されます。  
  
## <a name="see-also"></a>関連項目  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)



