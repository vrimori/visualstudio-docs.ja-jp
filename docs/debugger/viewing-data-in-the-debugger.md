---
title: "デバッガーでのデータのカスタム ビューを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e8f008ba3cde911ed5c21f281d30fda2a77bf824
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Visual Studio デバッガーでのデータのカスタム ビューを作成します。
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デバッガーには、プログラムの状態をチェックして変更できるように、さまざまなツールが用意されています。 ほとんどのツールは、中断モードだけで機能します。

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>変数ウィンドウと [データヒント] にデータのカスタム ビューを作成します。
 多くは、[デバッガー ウィンドウ](../debugger/debugger-windows.md)、ように、 **[自動変数]**と**ウォッチ**ウィンドウ、デバッグ中に変数を検査することができます。 ネイティブ型とし、デバッガー変数ウィンドウで、管理対象のオブジェクトの表示をカスタマイズする[データヒント](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)です。 独自のアプリケーションで作成する型を表示する便利なことができます。 詳細については、次を参照してください。[ネイティブ オブジェクトのカスタム ビューを作成する](../debugger/create-custom-views-of-native-objects.md)と[管理対象オブジェクトのカスタム ビューを作成](../debugger/create-custom-views-of-dot-managed-objects.md)です。
  
## <a name="create-custom-visualizers"></a>カスタム ビジュアライザーを作成します。  
 ビジュアライザーを使用すると、意味のある方法で、オブジェクトや変数の内容を表示できます。 Visual Studio デバッガー ビジュアライザーは虫眼鏡アイコンを使用して開くことができるさまざまなウィンドウを指します![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")です。 たとえば、HTML ビジュアライザーを使用すると、HTML 文字列を解釈してブラウザーに表示した場合と同様に表示できます。 ビジュアライザーには、DataTips、 **[ウォッチ]** ウィンドウ、 **[自動変数]** ウィンドウ、 **[ローカル]** ウィンドウ、または **[クイック ウォッチ]** ダイアログ ボックスからアクセスできます。 詳細については、次を参照してください。[カスタム ビジュアライザーを作成する](../debugger/create-custom-visualizers-of-data.md)です。
  
## <a name="see-also"></a>参照  
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [コマンド ウィンドウ](../ide/reference/command-window.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)