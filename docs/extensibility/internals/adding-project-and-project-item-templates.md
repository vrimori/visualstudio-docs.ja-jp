---
title: "プロジェクトを追加して、プロジェクト項目テンプレート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0201d2f282365a028b6251324b07276c995621ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="adding-project-and-project-item-templates"></a>プロジェクトとプロジェクト項目テンプレートを追加します。
独自のプロジェクトの種類を作成する場合は、標準を使用して新しいプロジェクトとプロジェクト アイテムを追加するサポートを指定する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]開発環境 (IDE) ダイアログ ボックスを統合します。 次のトピックでは、プロジェクトとプロジェクト アイテムを追加するためのさまざまな手法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プロジェクトのコンテキスト](../../extensibility/internals/project-context.md)  
 プロジェクトが、ほとんどの環境では新機能に関するコンテキスト情報を提供するについて説明します。  
  
 [プロジェクトの優先順位](../../extensibility/internals/project-priority.md)  
 プロジェクト項目はプロジェクトの使用を開くには、項目に関するあいまいさを回避できるようにするには、1 つのプロジェクトのメンバーでは通常について説明します。  
  
 [その他のファイル プロジェクト](../../extensibility/internals/miscellaneous-files-project.md)  
 プロジェクトのプロジェクト アイテムが開かれたときに使用するエディターの判断に再生ファイルを開くためのプロジェクトとの役割を使用できるエディターの 2 つの種類について説明します。  
  
 [プロジェクトと項目テンプレートの登録](../../extensibility/internals/registering-project-and-item-templates.md)  
 しくみについて説明しますと、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトを作成します。  
  
 [[新しい項目の追加] ダイアログ ボックスへの項目の追加](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 項目を追加するプロセスについて説明します、**新しい項目の追加** ダイアログ ボックス。  
  
 [[新しいプロジェクト] ダイアログ ボックスへの新しいディレクトリの追加](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 VSPackage で利用可能のカスタム テンプレートを格納する新しいディレクトリを登録する次の例を示します。  
  
 [[新しい項目の追加] ダイアログ ボックスへの新しいディレクトリの追加](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 ディレクトリの新しいセットを登録する次の例を示します、**新しい項目の追加** ダイアログ ボックス。  
  
 [プロジェクト システムを拡張するための IDE 定義コマンド](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 さまざまな種類のプロジェクト システムを拡張するために使用されるコマンドのアイテムを一覧表示します。  
  
 [プロジェクトの拡張に通常使用されるオブジェクトの CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 拡張に使用されるオブジェクトの Catid を一覧表示[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]、 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]、および[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]プロジェクト システムです。  
  
## <a name="related-sections"></a>関連項目  
 [方法: プロジェクト固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)  
 プロジェクトの特定のエディターに本質的にバインドされている項目を開く方法について説明を提供します。  
  
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)  
 標準のエディターを開くための手順を提供します。  
  
 [プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)  
 プロジェクトのサブタイプ概念説明のトピックへのリンクを提供します。 既存のプロジェクト サブタイプの拡張[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]プロジェクト。  
  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 新しいプロジェクトの種類を設計する方法に関する情報を提供するその他のトピックへのリンクを提供します。