---
title: "コマンドおよび相互運用機能アセンブリを使用してメニュー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee9fa1faa52afb2ea6d8154b4767fcab2cee0981
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>コマンドおよび相互運用機能アセンブリを使用してメニュー
相互運用機能アセンブリを使用してメニューやツールバーを実装する VSPackage 必要があります。  
  
-   通知、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) はサポートしているコマンドとかどうかは現在有効になっています。  
  
-   (コントラクト) コマンドを処理するための規則に従います。  
  
-   明示的にコマンドの処理を実装するいずれかを使用して、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイスです。  
  
 次に、これらのタスクを実行する方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [相互運用機能アセンブリを使用したコマンドのステータスの特定](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 VSPackage が、IDE に通知する方法について説明するコマンドに関するをサポートし、かどうか現在有効になっています。  
  
 [相互運用機能アセンブリでのコマンドのコントラクト](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 相互運用機能アセンブリを使用してコマンドを実装するすべての Vspackage で使用される基本的なコマンドのコントラクトの定義を提供します。  
  
 [実装](../../extensibility/internals/command-implementation.md)  
 VSPackage がコマンドを実装する方法の概要を示します。  
  
 [相互運用機能アセンブリ コマンド ハンドラーの登録](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 VSPackage にコマンド ハンドラーが提供されている IDE に通知するために必要なレジストリ エントリについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [可用性](../../extensibility/internals/command-availability.md)  
 VSPackage コマンドを使用できると処理のどのようなオブジェクトを判断する、IDE によって使用される条件について説明します。  
  
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 使用する UI を作成する方法の詳細については、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンドをサポートします。  
  
 [Vspackage のコマンド ルーティング](../../extensibility/internals/command-routing-in-vspackages.md)  
 正しいコマンド要求を持つオブジェクトを関連付けるために使用するプロセスの概要です。