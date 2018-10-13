---
title: ツールボックスの拡張 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: douge
ms.openlocfilehash: 444cf6b27179408414cc7df55d634497683004a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230335"
---
# <a name="extending-the-toolbox"></a>ツールボックスの拡張
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **ツールボックス** には、IDE のドラッグ アンド ドロップ メカニズムを利用してエディターとデザイナーに機能を提供するオブジェクトのコレクションが用意されています。  
  
 VSPackage が [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **ツールボックス**と連携して動作する方法には、次の 2 つの基本的な方法があります。  
  
-   VSPackage が、新しいデータ項目とコントロールを **ツールボックス**に追加します。  
  
-   VSPackage が、既存の **ツールボックス** 機能のターゲットまたはコンシューマーとなり、ドラッグ アンド ドロップ操作をサポートして、 **ツールボックス**の外観を構成します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: Windows フォームを使用するツールボックス コントロールを作成する](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Windows フォームのツールボックス コントロール テンプレートを使用して、ツールボックス コントロールを作成する方法を説明します。  
  
 [WPF ツールボックス コントロールの作成](../extensibility/creating-a-wpf-toolbox-control.md)  
 WPF ツールボックス コントロール テンプレートを使用して、ツールボックス コントロールを作成する方法を説明します。  
  
 [ツールボックスの管理](../misc/managing-the-toolbox.md)  
 VSPackage で **ツールボックス**のコンテンツと外観を管理する方法を記述します。  
  
## <a name="related-sections"></a>関連項目  
 [方法: ツールボックス ウィンドウの管理](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 **の統合開発環境 (IDE) で** ツールボックス [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] を使用する方法を説明します。  
  
 [方法: Control the Toolbox](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 オートメーション プログラミング モデルを使用して **ツールボックス** を管理する方法を説明します。  
  
 [Visual Studio の他の部分の拡張](../extensibility/extending-other-parts-of-visual-studio.md)  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] サービスを使用して、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]の他の部分に相当する UI 要素を作成する方法について説明します。