---
title: "プロジェクトおよびエディターの他のソース制御のガイドライン |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
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
ms.openlocfilehash: ee74f16c90dbf697732a490f895efb1a52233d80
ms.lasthandoff: 02/22/2017

---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>プロジェクトおよびエディターの他のソース制御のガイドライン
いくつかのプロジェクトおよびエディター ソース管理をサポートするために従う必要があるガイドラインがあります。  
  
## <a name="guidelines"></a>ガイドライン  
 プロジェクトまたはエディターでは、次をソース管理をサポートするためにもを実行する必要があります。  
  
|領域|プロジェクト|エディター|詳細|  
|----------|-------------|------------|-------------|  
|ファイルのプライベート コピー|x||環境には、ファイルのプライベート コピーがサポートしています。 各ユーザーがプロジェクトに参加している場合は、そのプロジェクト内のファイルの自分独自のプライベート コピーします。|  
|ANSI と Unicode の永続化|x|x|永続化コードを記述する場合は、ほとんどのソース管理プログラムは現在は Unicode をサポートしないために、ANSI 形式でファイルを保持します。|  
|ファイルを列挙します。|x||プロジェクト内のすべてのファイルの特定のリストを含める必要がありを使用してファイルの一覧を列挙できる必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> プロジェクトがを通じて項目名に公開することはもその<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>実装およびサポートの名前検索 (特殊なファイルを含む) をその<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>実装</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>。|  
|テキストの形式|x|x|可能であれば、ファイルは、異なるバージョンの結合をサポートするテキスト形式でなければなりません。 テキスト形式でないファイルは、ファイルの他のバージョンと後でマージすることはできません。 任意のテキスト形式は XML です。|  
|参照に基づく|x||参照ベースのプロジェクトは、ソース管理で簡単にサポートされます。 ただし、ディレクトリ ベースのプロジェクトは、プロジェクトは、それらのファイルがディスクに存在するかどうかに関係なく、必要に応じてそのファイルの一覧を作成できる限りもソース管理でサポートされます。 ソース管理からプロジェクトを開くときに&1; つ目のファイルの前に、プロジェクト ファイルが終了します。|  
|予測可能な順序でオブジェクトとプロパティを永続化します。|x|x|マージするためのアルファベット順などの予測可能な順序で、ファイルを保持します。|  
|再読み込み|x|x|ファイルがディスクに変更されると、エディターは、再読み込みできる必要があります。 環境によって呼び出すことでのデータが再度読み込まソース管理に参加すると、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>実装</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>。 IVsQueryEditQuerySave を呼び出したときに、チェック アウトが発生している最も困難な再読み込みの場合::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>や情報が処理されます</xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>。 ただし、再読み込みコードは、このような状況で実行できる必要があります。<br /><br /> 環境では、プロジェクト ファイルが自動的に再読み込みします。 ただし、プロジェクトを実装する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>プロジェクト ファイルを再読み込みをサポートするために階層が入れ子になったに入れ子になった場合</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理をサポートします。](../../extensibility/internals/supporting-source-control.md)
