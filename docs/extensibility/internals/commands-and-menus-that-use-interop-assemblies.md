---
title: 相互運用機能アセンブリを使用するコマンドとメニュー |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2212d9eb38487bf824fd8df3c497d9f256379c10
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907808"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>相互運用機能アセンブリを使用するコマンドとメニュー
相互運用機能アセンブリを使用してメニューやツールバーを実装する VSPackage にする必要があります。  
  
- 通知、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) についてサポートしているコマンドやかどうかが現在有効にします。  
  
- (コントラクト) コマンドを処理するための規則に従います。  
  
- いずれかを使用してコマンド処理を明示的に実装、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイス。  
  
  次のセクションでは、これらのタスクを実行する方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [相互運用機能アセンブリを使用してコマンドのステータスを確認します。](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 VSPackage に IDE がユーザーに通知方法について説明します。 コマンドについてサポートし、かどうかが現在有効になっています。  
  
 [相互運用機能アセンブリでのコマンドのコントラクト](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 相互運用機能アセンブリを使用してコマンドを実装するすべての Vspackage で使用される基本的なコマンドのコントラクトの定義を提供します。
  
 [コマンドの実装](../../extensibility/internals/command-implementation.md)  
 VSPackage のコマンドを実装する方法の概要を示します。  
  
 [相互運用機能アセンブリ コマンド ハンドラーを登録します。](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 VSPackage がコマンド ハンドラーを提供することを IDE に通知するために必要なレジストリ エントリについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [利用可能なコマンド](../../extensibility/internals/command-availability.md)  
 VSPackage のコマンドに利用をどのようなオブジェクトには、それらは処理を決定する、IDE で使用される条件について説明します。  
  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 使用する UI を作成する方法の詳細については、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンドをサポートします。  
  
 [Vspackage のコマンド ルーティング](../../extensibility/internals/command-routing-in-vspackages.md)  
 適切なコマンドの要求を持つオブジェクトを関連付けるために使用するプロセスの概要。