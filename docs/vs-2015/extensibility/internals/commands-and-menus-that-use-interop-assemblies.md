---
title: 相互運用機能アセンブリを使用するコマンドとメニュー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d050f2e96eb78462f9e5e77504a365d17ed01d6d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533517"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>相互運用機能アセンブリを使用するコマンドとメニュー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[コマンドとメニューを使用して相互運用機能アセンブリ](https://docs.microsoft.com/visualstudio/extensibility/internals/commands-and-menus-that-use-interop-assemblies)します。  
  
相互運用機能アセンブリを使用してメニューやツールバーを実装する VSPackage にする必要があります。  
  
-   通知、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]統合開発環境 (IDE) についてサポートしているコマンドやかどうかが現在有効にします。  
  
-   (コントラクト) コマンドを処理するための規則に従います。  
  
-   いずれかを使用してコマンド処理を明示的に実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイス。  
  
 次に、これらのタスクを実行する方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [相互運用機能アセンブリを使用したコマンドのステータスの特定](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 VSPackage に IDE がユーザーに通知方法について説明します。 コマンドについてサポートし、かどうかが現在有効になっています。  
  
 [相互運用機能アセンブリでのコマンドのコントラクト](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 相互運用機能アセンブリを使用してコマンドを実装するすべての Vspackage で使用される基本的なコマンドのコントラクトの定義を提供します。  
  
 [実装](../../extensibility/internals/command-implementation.md)  
 VSPackage のコマンドを実装する方法の概要を示します。  
  
 [相互運用機能アセンブリ コマンド ハンドラーの登録](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 VSPackage がコマンド ハンドラーを提供することを IDE に通知するために必要なレジストリ エントリについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [利用可能性](../../extensibility/internals/command-availability.md)  
 VSPackage のコマンドに利用をどのようなオブジェクトには、それらは処理を決定する、IDE で使用される条件について説明します。  
  
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 使用する UI を作成する方法の詳細については、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]コマンドをサポートします。  
  
 [Vspackage のコマンド ルーティング](../../extensibility/internals/command-routing-in-vspackages.md)  
 適切なコマンドの要求を持つオブジェクトを関連付けるために使用するプロセスの概要。

