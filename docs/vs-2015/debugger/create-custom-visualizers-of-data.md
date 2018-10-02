---
title: データのカスタム ビジュアライザーを作成する |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a025068d1657d9feb569a77731aa8bab517bae2f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544694"
---
# <a name="create-custom-visualizers-of-data"></a>データのカスタム ビジュアライザーを作成します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[データのカスタム ビジュアライザーの作成](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)です。  
  
ビジュアライザーのコンポーネントである、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]デバッガー ユーザー インターフェイス。 A*ビジュアライザー*  ダイアログ ボックスまたはそのデータ型に適した方法で変数またはオブジェクトを表示する別のインターフェイスを作成します。 たとえば、HTML ビジュアライザーは、HTML 文字列を解釈し、ブラウザー ウィンドウに表示されるとおりに結果を表示します。また、ビットマップ ビジュアライザーは、ビットマップ構造体を解釈し、ビットマップが表すグラフィックを表示します。 一部のビジュアライザーでは、データを表示するだけでなく、変更することもできます。  
  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] デバッガーには、6 つの標準的なビジュアライザーが用意されています。 これらは、テキスト、HTML、XML、および JSON ビジュアライザー、文字列オブジェクトのすべての作業WPF オブジェクトのビジュアル ツリー; のプロパティを表示するため、WPF ツリー ビジュアライザーで、データセット、データ ビュー、および DataTable オブジェクトの動作であるデータセット visualizer です。 その他のビジュアライザーは、今後 Microsoft Corporation からダウンロード可能になる場合があり、サード パーティやコミュニティからも入手できます。 また、独自のビジュアライザーを記述して、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] デバッガーにインストールすることもできます。  
  
> [!NOTE]
>  **ストア**アプリ、標準のテキストのみ HTML、XML、および JSON ビジュアライザーがサポートされています。 カスタム (ユーザーが作成した) ビジュアライザーはサポートされていません。  
  
 デバッガーでは、ビジュアライザーは虫眼鏡アイコンで表されます。 虫眼鏡アイコンを表示、**データヒント**デバッガー変数ウィンドウ、または、 **[クイック ウォッチ]** ダイアログ ボックスで、データ型に適したビジュアライザーを選択する虫眼鏡をクリックすることができます対応するオブジェクト。  
  
 ビジュアライザーは、.NET Compact Framework ではサポートされていません。  
  
> [!NOTE]
>  デバッガー ビジュアライザーでは、部分信頼アプリケーションが許可する以上の特権が必要です。 この結果、部分信頼コードで動作が停止した場合、ビジュアライザーは読み込まれません。 ビジュアライザーを使用してデバッグするには、完全信頼コードを実行する必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法 : ビジュアライザーを記述する](../debugger/how-to-write-a-visualizer.md)  
  
 [チュートリアル : C# でビジュアライザーを記述する](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [方法 : ビジュアライザーをインストールする](../debugger/how-to-install-a-visualizer.md)  
  
 [方法 : ビジュアライザーをテストおよびデバッグする](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [ビジュアライザー API リファレンス](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>関連項目  
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)



