---
title: デバッガーでのデータのカスタム ビューの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/27/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02bb65aa2b0601315a3f5dec2cc9459af210db3e
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177673"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Visual Studio デバッガーでのデータのカスタム ビューを作成します。
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーには、プログラムの状態をチェックして変更できるように、さまざまなツールが用意されています。 ほとんどのツールは、中断モードだけで機能します。

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>変数ウィンドウとデータヒントでのデータのカスタム ビューを作成します。
 多くは、[デバッガー ウィンドウ](../debugger/debugger-windows.md)など、 **[自動変数]** と**ウォッチ**ウィンドウ、デバッグ中に変数を検査することができます。 ネイティブ型とし、デバッガー変数ウィンドウで、管理対象のオブジェクトの表示をカスタマイズする[データヒント](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)します。 独自のアプリケーションで作成する型を表示する便利なことができます。 詳細については、次を参照してください。[ネイティブ オブジェクトのカスタム ビューを作成](../debugger/create-custom-views-of-native-objects.md)と[マネージ オブジェクトのカスタム ビューを作成する](../debugger/create-custom-views-of-dot-managed-objects.md)します。
  
## <a name="create-custom-visualizers"></a>カスタム ビジュアライザーを作成します。  
 ビジュアライザーを使用すると、わかりやすい方法でオブジェクトや変数の内容を表示できます。 Visual Studio デバッガー ビジュアライザーは虫眼鏡アイコンを使用して開くことができる別の windows を指します![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")します。 たとえば、HTML ビジュアライザーを使用すると、HTML 文字列を解釈してブラウザーに表示した場合と同様に表示できます。 ビジュアライザーには、DataTips、 **[ウォッチ]** ウィンドウ、 **[自動変数]** ウィンドウ、 **[ローカル]** ウィンドウ、または **[クイック ウォッチ]** ダイアログ ボックスからアクセスできます。 詳細については、次を参照してください。[カスタム ビジュアライザーを作成する](../debugger/create-custom-visualizers-of-data.md)します。
  
## <a name="see-also"></a>関連項目  
 [デバッガーの基本事項](../debugger/getting-started-with-the-debugger.md)   
 [コマンド ウィンドウ](../ide/reference/command-window.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)