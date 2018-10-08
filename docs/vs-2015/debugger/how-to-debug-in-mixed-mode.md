---
title: '方法: 混合モードでデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce056b60a3e080490a2ad60f4aee5a7b5c8dd63
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534417"
---
# <a name="how-to-debug-in-mixed-mode"></a>方法 : 混合モードでデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 混合モードでデバッグ](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-in-mixed-mode)します。  
  
ここでは、マネージド コードとネイティブ コードの両方をデバッグする方法について説明します。これは、混合モード デバッグとも呼ばれます。 DLL またはアプリケーションがネイティブ コードで記述されているかどうかによって、2 つのデバッグ シナリオがあります。  
  
-   DLL を呼び出す呼び出し元のアプリケーションがネイティブ コードで記述されている。 この場合は、DLL がマネージド DLL であり、マネージド デバッガーとネイティブ デバッガーの両方を有効にしてデバッグする必要があります。 これを確認するには、 **\<プロジェクト > プロパティ ページ** ダイアログ ボックス。 DLL プロジェクトからデバッグを開始するか、呼び出し元のアプリケーション プロジェクトからデバッグを開始するかによって、確認方法は異なります。  
  
-   DLL を呼び出す呼び出し元のアプリケーションがマネージド コードで記述され、DLL がネイティブ コードで記述されている。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-enable-mixed-mode-debugging"></a>混合モードのデバッグを有効にするには  
  
1.  **ソリューション エクスプ ローラー**プロジェクトを選択します。  
  
2.  **ビュー**  メニューのをクリックして**プロパティ ページ**します。  
  
3.  **\<プロジェクト > プロパティ ページ** ダイアログ ボックスで、展開、**構成プロパティ**ノードをクリックして**デバッグ**します。  
  
4.  設定**デバッガーの種類**に**混合**または**自動**します。  
  
## <a name="see-also"></a>関連項目  
 [方法 : DLL プロジェクトからデバッグする](../debugger/how-to-debug-from-a-dll-project.md)



