---
title: "コマンドと相互運用機能アセンブリを使用してメニュー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c0d2cf9218743ec21121d849482e5a3086b36ab2
ms.lasthandoff: 02/22/2017

---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>コマンドと相互運用機能アセンブリを使用してメニュー
VSPackage を相互運用機能アセンブリを使用して、メニューやツールバーを実装する必要があります。  
  
-   通知、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) はサポートしているコマンドとするかどうかは現在有効になっています。  
  
-   (コントラクト) のコマンドを処理するための規則に従います。  
  
-   いずれかを使用してコマンドの処理を明示的に実装する、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。  
  
 次に、これらのタスクを実行する方法を説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [相互運用機能アセンブリを使用してコマンドのステータスの特定](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 VSPackage が IDE にどのように通知する方法について説明するコマンドの詳細をサポートし、かどうかは現在有効になっています。  
  
 [相互運用機能アセンブリでのコマンドのコントラクト](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 相互運用機能アセンブリを使用してコマンドを実装するすべての VSPackages で使用される基本的なコマンドのコントラクトの定義を提供します。  
  
 [実装](../../extensibility/internals/command-implementation.md)  
 VSPackage でコマンドがどのように実装する方法の概要を示します。  
  
 [相互運用機能アセンブリ コマンド ハンドラーを登録します。](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 VSPackage でコマンド ハンドラーを提供する、IDE に通知するために必要なレジストリ エントリについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [可用性](../../extensibility/internals/command-availability.md)  
 VSPackage のコマンドが利用でき、どのようなオブジェクトには、それらは処理を決定する IDE によって使用される条件について説明します。  
  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 使用する UI を作成する方法の詳細については、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンドをサポートします。  
  
 [Vspackage でルーティング コマンド](../../extensibility/internals/command-routing-in-vspackages.md)  
 正しいコマンド要求を持つオブジェクトを関連付けるために使用するプロセスの概要です。
