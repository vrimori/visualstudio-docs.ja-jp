---
title: "方法: ステータス バーの更新 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシー - ステータス バーを更新します。"
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 方法: ステータス バーの更新
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**ステータス バー**  は一つ以上のステータス テキストの行またはインジケーターなど多くのアプリケーション ウィンドウの下にあるコントロール バーです。  
  
### ステータス バーを更新するには  
  
1.  エディターに用意されているフォーム ビューとコード ビューなど個々のビュー オブジェクト DocView \(\) の <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> を実行します。  
  
2.  IDE が <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> を呼び出すと<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> のメソッドを呼び出して  **ステータス バー**  情報を更新します。  
  
    > [!NOTE]
    >  IDE ではドキュメント ウィンドウがアクティブな場合にのみ <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> を呼び出します。  時間の残りの部分ではエディターの状態が変更されたときにドキュメント ウィンドウがアクティブであるか **ステータス バー**  の情報を更新する必要があります。  
  
## 信頼性の高いプログラミング  
 **ステータス バー**  には4 種類の別個のフィールドが含まれています :  
  
-   ステータス テキスト  
  
-   進行状況バー  
  
-   アニメーション化されたアイコン  
  
-   エディターの情報  
  
 詳細については、「[ステータス バー](/visual-cpp/mfc/status-bars)」を参照してください。  
  
 IDE で自動的にドキュメント ウィンドウがアクティブになると <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> の実装の <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> のメソッドを呼び出します。  
  
 VSPackage の実装はステータス バーにステータス テキストを更新する必要があります。  IDE が " 準備完了 " にステータス テキスト フィールドがアイドル時間の文字列 \(""\) を格納できます。この文字列をリセットします。  
  
## 参照  
 [ステータス バー](/visual-cpp/mfc/status-bars)