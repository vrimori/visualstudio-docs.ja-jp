---
title: Visual Studio での階層 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 20e8dcb947b84652f818ab38ed441e39e27942e9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033402"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio での階層
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) とプロジェクトが表示されます、*階層*します。 IDE では、階層は、各ノードが関連付けられているプロパティのセットを持つノードのツリーです。 A*プロジェクト階層*はプロジェクトのアイテム、アイテムのリレーションシップ、および項目の関連付けられているプロパティおよびコマンドを保持するコンテナーです。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、階層のインターフェイスを使用してプロジェクトの階層を管理する<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>インターフェイスは、標準のコマンド ハンドラーではなく、適切な階層ウィンドウにプロジェクト項目から実行するコマンドをリダイレクトします。  
  
## <a name="project-hierarchies"></a>プロジェクト階層  
 プロジェクトの各階層には、表示して編集する項目が含まれています。 これらの項目は、プロジェクトの種類によって異なります。 たとえば、データベース プロジェクトには、ストアド プロシージャ、データベース ビュー、およびデータベースのテーブルが含まれます。 プログラミング言語のプロジェクトでは、その一方で、可能性がありますが含まれますソース ファイルおよびビットマップとダイアログ ボックスのリソース ファイル。 説明するいくつかの柔軟性がプロジェクト階層を作成するときに、階層はネストできます。  
  
 新しいプロジェクトの種類を作成するときに、プロジェクトの種類が編集可能な項目の完全なセットを制御します。 ただし、項目を持たない編集サポートがプロジェクトに含めることができます。 たとえば、Visual C プロジェクトは、場合でも、Visual C では、任意のエディターのカスタマイズされた HTML ファイルの種類を提供しません、HTML ファイルを含めることができます。  
  
 階層では、含まれるアイテムの永続性を管理します。 階層の実装では、階層内の項目の持続性に影響を与えるすべての特殊なプロパティを制御する必要があります。 など、項目は、ファイルではなく、リポジトリ内のオブジェクトを表す、階層の実装はこれらのオブジェクトの永続化を制御する必要があります。 IDE 自体が、階層、ユーザー入力に準拠している項目を保存するように指示しますが、IDE は、それらの項目を保存するために必要なすべてのアクションを制御しません。 代わりに、プロジェクトが制御します。  
  
 ユーザーが項目を開く、エディターで、その項目を制御する階層が選択され、アクティブな階層になります。 選択した階層は、項目を操作する使用可能なコマンドのセットを決定します。 ユーザーの現在のコンテキストを反映するように階層をこの方法でユーザーのフォーカスを追跡できます。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)   
 [選択と、IDE で通貨](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [VSSDK のサンプル](http://aka.ms/vs2015sdksamples)