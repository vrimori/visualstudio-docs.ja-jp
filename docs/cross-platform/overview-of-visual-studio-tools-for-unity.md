---
title: "Visual Studio Tools for Unity の概要 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 4
author: ghogen
ms.author: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 2ae1ef56f40106321dd514b3e42e54be2afa7efd
ms.contentlocale: ja-jp
ms.lasthandoff: 05/13/2017

---
# Visual Studio Tools for Unity の概要
<a id="overview-of-visual-studio-tools-for-unity" class="xliff"></a>
このセクションでは、Visual Studio Tools for Unity から提供される機能の概要と、Unity を使用する開発の生産性を向上させる方法について説明します。  
  
 Visual Studio tools Unity (*VSTU*) を利用すると、Visual Studio を使用して C# でゲームとエディター スクリプトを記述した後、強力なデバッガーを使用してエラーを検出して修正できます。 VSTU の最新リリースでは、Unity の ShaderLab シェーダー言語の構文の色分け、デバッガーの視覚化機能の向上、および、MonoBehavior ウィザードによるコード生成の機能強化などが行われました。 また、VSTU により、Unity のプロジェクト ファイル、コンソール メッセージ、およびゲームを開始する機能が Visual Studio に統合されるため、コードの記述中に Unity エディターとの間で切り替える手間を少なくできます。  
  
 これらの機能に関する詳細を、このあと説明します。  
  
## Unity との統合
<a id="integration-with-unity" class="xliff"></a>  
 Unity エディターと Visual Studio を常に切り替えながら作業しなければならないとすると、Visual Studio Tools for Unity は生産性向上ツールであるとは言えません。 そのような理由から、Visual Studio Tools for Unity では、Visual Studio を離れずに簡単に作業できるようになっています。  
  
-   **Unity プロジェクト エクスプローラー**を使用すると、Unity エディターに表示されるのと同じ階層構造で Visual Studio から Unity プロジェクト全体を見ることができます。  
  
-   Unity コンソールとの統合により、Visual Studio のエラー ウィンドウに Unity コンソールからの出力が表示されます。  
  
-   Visual Studio からゲームのデバッグを開始できます。Unity に切り替える必要はなく、F5 キーを押すだけです。  
  
## 優れたデバッグ機能
<a id="superior-debugging" class="xliff"></a>  
 スタンドアロンで実行されているか Unity エディターで実行されているかに関係なく、Visual Studio の強力なデバッガーを Unity ゲームに接続して、C# スクリプトと DLL をデバッグできます。 Visual Studio によって提供されるすべてのデバッグ機能を使用できます。  
  
-   ブレークポイント (条件付きブレークポイントを含む)。  
  
-   [ウォッチ] ウィンドウでの複雑な式の評価。  
  
-   変数および引数の値の検査と変更。  
  
-   複雑なオブジェクトやデータ構造体へのドリルダウン。  
  
 さらに、ネットワーク上の別のコンピューターで実行されている Unity ゲームであっても、デバッグできます。  
  
## 生産性
<a id="productivity" class="xliff"></a>  
 C# コードの記述とリファクタリングについての Visual Studio の確立された生産性に加えて、Visual Studio Tools for Unity は Unity 開発者のために追加の生産性機能を提供します。  
  
-   Unity の ShaderLab 言語の構文が色分け表示されるため、バグになる前にシェーダーで間違いを見つけるために役立ちます。 これは、ShaderLab ファイルを Visual Studio で開くだけで機能します。  
  
-   MonoBehavior ウィザードを使用すると、Unity の動作の一覧を参照し、使い慣れていない動作であっても、定型的なコードを作成できます。 Ctrl + Shift + M キーを押します。  
  
-   よく使用する Unity の動作に慣れてきたら、クイック MonoBehavior ウィザードを使用して簡単に入力できます。 Ctrl + ALT + Q キーを押します。  
  
-   Visual Studio から Unity のドキュメントにアクセスできます。 説明を読みたい API 呼び出しを強調表示し、Ctrl + ALT+M を押し、Ctrl + H を押します。  
  
-   これらの機能すべてと、その他の機能は、キーボード ショートカットでアクセスできます。  
  
## Visual Studio Tools for Unity の API
<a id="visual-studio-tools-for-unity-api" class="xliff"></a>  
 提供されている API を使用して、Visual Studio Tools for Unity の動作のカスタマイズや拡張を行えます。  
  
-   Visual Studio Tools for Unity では、Unity コンソールを Visual Studio にストリーミングできるよう、Unity にログ コールバックを登録します。 情報を記録するエディター スクリプトがあれば、同じコールバックにそれらのスクリプトをプラグインして、Visual Studio にメッセージを送信できます。 詳細については、ログのコールバックの例を参照してください。  
  
-   Visual Studio Tools for Unity がプロジェクト ファイルを生成する方法を変更するには、Unity のスタイル コールバック ProjectFileGeneration を使用します。 詳細については、プロジェクト ファイル生成の例を参照してください。  
  
## 関連項目
<a id="see-also" class="xliff"></a>  
 [Unity ホームページ](http://unity3d.com)
