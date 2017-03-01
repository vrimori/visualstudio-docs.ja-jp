---
title: "Visual Studio での階層 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 14
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
ms.openlocfilehash: ca8fa51a14f38dcd651f26e8ed10ca48d670f37b
ms.lasthandoff: 02/22/2017

---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio での階層
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) とプロジェクトの表示、*階層*します。 IDE では、階層は、各ノードが関連付けられているプロパティのセットには、ノードのツリーです。 A*プロジェクトの階層*プロジェクトのアイテム、アイテムのリレーションシップ、および項目の関連付けられているプロパティおよびコマンドを保持するコンテナーです。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>階層インターフェイスを使用してプロジェクトの階層を管理します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイスは、標準的なコマンド ハンドラーの代わりに適切な階層 ウィンドウにプロジェクト項目から実行するコマンドをリダイレクトします</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>。  
  
## <a name="project-hierarchies"></a>プロジェクト階層  
 各プロジェクトの階層構造には、表示および編集できる項目が含まれています。 これらの項目は、プロジェクトの種類によって異なります。 たとえば、データベース プロジェクトには、ストアド プロシージャ、ビューのデータベースおよびデータベースのテーブルが含まれます。 プログラミング言語のプロジェクトでは、その一方で、可能性がありますが含まれますソース ファイルおよびビットマップとダイアログ ボックスのリソース ファイル。 これをある程度柔軟追加したプロジェクトの階層構造を作成するときに、階層はネストできます。  
  
 新しいプロジェクトの種類を作成するときに、プロジェクトの種類はで、編集可能なアイテムの完全なセットを制御します。 ただし、プロジェクトでは、項目を持たない編集のサポートを含めることができます。 たとえば、Visual C プロジェクトは Visual C が HTML ファイルの種類の任意のカスタム エディターを提供しない場合でも HTML ファイルを含めることができます。  
  
 階層では、含まれるアイテムの永続化を管理します。 階層の実装には、階層内の項目の持続性に影響を与える特別なプロパティを制御する必要があります。 など、アイテムは、ファイルではなくリポジトリ内のオブジェクトを表している場合階層の実装はこれらのオブジェクトの永続化を制御する必要があります。 IDE により、ユーザー入力に対応してアイテムを保存する階層が、IDE は、それらの項目を保存するために必要なすべてのアクションを制御しません。 代わりに、プロジェクトがコントロールであります。  
  
 エディターで、ユーザーが項目を開くと、その項目を制御する階層が選択され、アクティブな階層になります。 選択した階層では、アイテムを操作する使用可能なコマンドのセットを決定します。 ユーザーの現在のコンテキストを反映するように階層をこの方法でユーザーのフォーカスを追跡できます。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)   
 [選択と、IDE 内の通貨](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [VSSDK のサンプル](../../misc/vssdk-samples.md)
