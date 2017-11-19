---
title: "Visual Studio での階層 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a651267ed279fa5efaf14efb4f1f866794c5cc3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio での階層
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) としてのプロジェクトが表示されます、*階層*です。 IDE では、階層は、各ノードが関連付けられているプロパティのセットを持つノードのツリーです。 A*階層をプロジェクト*プロジェクトのアイテム、アイテムのリレーションシップ、および項目の関連付けられているプロパティおよびコマンドを保持するコンテナーです。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、階層インターフェイスを使用してプロジェクトの階層を管理する<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>です。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイスは、標準のコマンド ハンドラーではなく、適切な階層ウィンドウにプロジェクト項目から実行するコマンドをリダイレクトします。  
  
## <a name="project-hierarchies"></a>プロジェクト階層  
 プロジェクトの各階層には、表示および編集できる項目が含まれています。 これらの項目は、プロジェクトの種類によって異なります。 たとえば、データベース プロジェクトには、ストアド プロシージャ、ビューのデータベース、およびデータベースのテーブルが含まれます。 プログラミング言語のプロジェクトでは、その一方で、可能性がありますが含まれますソース ファイルおよびビットマップとダイアログ ボックスのリソース ファイル。 提供するいくつかの柔軟性がプロジェクト階層を作成するときに、階層はネストできます。  
  
 新しいプロジェクトの種類を作成するときに、プロジェクトの種類で編集可能なアイテムの完全なセットを制御します。 ただし、プロジェクトでは、項目を持たない編集のサポートを含めることができます。 たとえば、Visual C プロジェクトは、場合でも、Visual C は、HTML ファイルの種類を任意のカスタム エディターを提供しません、HTML ファイルを含めることができます。  
  
 階層は、含まれるアイテムの永続化を管理します。 階層の実装には、階層内のアイテムの持続性に影響する任意の特殊なプロパティを制御する必要があります。 たとえば、項目は、ファイルではなくリポジトリ内のオブジェクトを表している場合階層実装はそれらのオブジェクトの永続化を制御する必要があります。 IDE が、階層、ユーザー入力に準拠して項目を保存するように指示が IDE でこれらの項目を保存するために必要なすべてのアクションを制御しません。 代わりに、プロジェクトは、コントロールでです。  
  
 エディターで、ユーザーが項目を開くと、その項目を制御する階層が選択され、アクティブな階層になります。 選択した階層では、一連の項目に作用するコマンドを決定します。 この方法でユーザーのフォーカスを追跡するには、ユーザーの現在のコンテキストを反映するように階層が有効にします。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)   
 [選択範囲と、IDE の通貨](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [VSSDK のサンプル](http://aka.ms/vs2015sdksamples)