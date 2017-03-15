---
title: "方法 : Visual Basic 開発者設定が適用されたビルド構成を管理する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ビルド構成の詳細"
  - "ビルド (Visual Basic 開発者設定を使用して)"
  - "デバッグ ビルド"
  - "MSBuild, デバッグ ビルド"
  - "MSBuild, リリース ビルド"
  - "リリース ビルド"
  - "Visual Studio, ビルド (Visual Basic 設定を使用して)"
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# 方法 : Visual Basic 開発者設定が適用されたビルド構成を管理する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

既定では、すべての詳細ビルド構成オプションは非表示になっており、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 開発者設定が適用されています。  ここでは、これらの設定を手動で有効にする方法を説明します。  
  
## 詳細ビルド構成を有効にする  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 開発者設定の既定では、**\[構成マネージャー\]** ダイアログ ボックスおよび [プロジェクト デザイナー](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)の **\[構成\]** リストと **\[プラットフォーム\]** リストを開くオプションは非表示にされています。  
  
#### 詳細ビルド構成を有効にするには  
  
1.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
2.  **\[プロジェクトおよびソリューション\]** を展開し、**\[全般\]** をクリックします。  
  
    > [!NOTE]
    >  **\[全般\]** ノードは、**\[すべての設定を表示\]** チェック ボックスがオフの場合でも表示されます。  すべての使用できるオプションを表示するには、**\[すべての設定を表示\]** チェック ボックスをオンにします。  
  
3.  **\[ビルド構成の詳細を表示\]** をクリックします。  
  
4.  **\[OK\]** をクリックします。  
  
     これで、**\[ビルド\]** メニューの **\[構成マネージャー\]**、およびプロジェクト デザイナーの **\[構成\]** リストと **\[プラットフォーム\]** リストが使用できるようになります。  
  
## 参照  
 [ビルド構成について](../ide/understanding-build-configurations.md)   
 [Visual Studio でのアプリケーションのビルド](../ide/compiling-and-building-in-visual-studio.md)