---
title: "方法: 混合モードでデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e319f0e6c9ca6197930858407a2177e9fe246907
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-in-mixed-mode"></a>方法 : 混合モードでデバッグする
ここでは、マネージ コードとネイティブ コードの両方をデバッグする方法について説明します。これは、混合モード デバッグとも呼ばれます。 DLL またはアプリケーションがネイティブ コードで記述されているかどうかによって、2 つのデバッグ シナリオがあります。  
  
-   DLL を呼び出す呼び出し元のアプリケーションがネイティブ コードで記述されている。 この場合は、DLL がマネージ DLL であり、マネージ デバッガーとネイティブ デバッガーの両方を有効にしてデバッグする必要があります。 これをチェックすることができます、 **\<プロジェクト > プロパティ ページ** ダイアログ ボックス。 DLL プロジェクトからデバッグを開始するか、呼び出し元のアプリケーション プロジェクトからデバッグを開始するかによって、確認方法は異なります。  
  
-   DLL を呼び出す呼び出し元のアプリケーションがマネージ コードで記述され、DLL がネイティブ コードで記述されている。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

呼び出し元のアプリのプロジェクトへのアクセスを持っていない場合は、DLL プロジェクトから DLL をデバッグすることができます。 詳細については、「 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)」を参照してください。 不要を使用するだけの DLL プロジェクトをデバッグするために組み合わせるです。
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>混合モード デバッグ (C++ の呼び出し元アプリケーション) を有効にするには  
  
1.  **ソリューション エクスプ ローラー**、ネイティブ プロジェクトを選択します。
  
2.  **ビュー**  メニューのをクリックして**プロパティ ページ**です。
  
3.  **\<プロジェクト > プロパティ ページ** ダイアログ ボックスで、展開、**構成プロパティ**ノードをクリックして**デバッグ**です。  
  
4.  設定**デバッガーの種類**に**混合**または**自動**です。

    ![混合モード デバッグを有効にする](../debugger/media/dbg-mixed-mode-from-native.png "混合モード デバッグを有効にします。")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>混合モード デバッグ (c# または VB 呼び出し元アプリケーション) を有効にするには  
  
1.  **ソリューション エクスプ ローラー**、管理対象のプロジェクトを選択します。  
  
2.  **ビュー**  メニューのをクリックして**プロパティ ページ**です。  
  
3.  **\<プロジェクト > プロパティ ページ**ダイアログ ボックスで、**デバッグ**、タブをクリックし**ネイティブ コードのデバッグを有効にします。**

    ![ネイティブ コードのデバッグを有効にする](../debugger/media/dbg-mixed-mode-from-csharp.png "ネイティブ コードのデバッグを有効にします。")
  
## <a name="see-also"></a>関連項目  
 [方法 : DLL プロジェクトからデバッグする](../debugger/how-to-debug-from-a-dll-project.md)