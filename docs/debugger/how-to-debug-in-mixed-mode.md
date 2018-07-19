---
title: '方法: 混合モードでデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 834288c063a4bc0d830f121dcb8589b509c61bcf
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256163"
---
# <a name="how-to-debug-in-mixed-mode"></a>方法 : 混合モードでデバッグする
ここでは、マネージド コードとネイティブ コードの両方をデバッグする方法について説明します。これは、混合モード デバッグとも呼ばれます。 DLL またはアプリケーションがネイティブ コードで記述されているかどうかによって、2 つのデバッグ シナリオがあります。  
  
-   DLL を呼び出す呼び出し元のアプリケーションがネイティブ コードで記述されている。 この場合は、DLL がマネージド DLL であり、マネージド デバッガーとネイティブ デバッガーの両方を有効にしてデバッグする必要があります。 これを確認するには、 **\<プロジェクト > プロパティ ページ** ダイアログ ボックス。 DLL プロジェクトからデバッグを開始するか、呼び出し元のアプリケーション プロジェクトからデバッグを開始するかによって、確認方法は異なります。  
  
-   DLL を呼び出す呼び出し元のアプリケーションがマネージド コードで記述され、DLL がネイティブ コードで記述されている。 次の手順を説明するチュートリアルについては、次を参照してください。[マネージとネイティブ コード デバッグ](../debugger/how-to-debug-managed-and-native-code.md)します。
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

呼び出し元のアプリのプロジェクトへのアクセスを持っていない場合は、DLL プロジェクトから DLL をデバッグできます。 詳細については、「 [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md)」を参照してください。 混合デバッグ、DLL プロジェクトだけに使用する必要ありません。
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>混合モード デバッグ (C++ の呼び出し元のアプリ) を有効にするには  
  
1.  **ソリューション エクスプ ローラー**、ネイティブ プロジェクトを選択します。
  
2.  **ビュー**  メニューのをクリックして**プロパティ ページ**します。
  
3.  **\<プロジェクト > プロパティ ページ** ダイアログ ボックスで、展開、**構成プロパティ**ノードをクリックして**デバッグ**します。  
  
4.  設定**デバッガーの種類**に**混合**または**自動**します。

    ![混合モード デバッグを有効にする](../debugger/media/dbg-mixed-mode-from-native.png "混合モード デバッグを有効にします。")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>混合モード デバッグ (c# または VB 呼び出し元のアプリ) を有効にするには  
  
1.  **ソリューション エクスプ ローラー**、管理対象のプロジェクトを選択します。  
  
2.  **ビュー**  メニューのをクリックして**プロパティ ページ**します。  
  
3.  **\<プロジェクト > プロパティ ページ**ダイアログ ボックスで、**デバッグ**、タブを選び**ネイティブ コードのデバッグを有効にします。**

    ![ネイティブ コードのデバッグを有効にする](../debugger/media/dbg-mixed-mode-from-csharp.png "ネイティブ コードのデバッグを有効にします。")
  
## <a name="see-also"></a>関連項目  
 [方法 : DLL プロジェクトからデバッグする](../debugger/how-to-debug-from-a-dll-project.md)