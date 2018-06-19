---
title: プロジェクトおよびエディターに対して追加のソース コントロール ガイドライン |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e39c8fcc78712f0f8d9b799789751c16f343ada6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129282"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>プロジェクトおよびエディターに対して追加のソース コントロールのガイドライン
いくつかのプロジェクトおよびエディター ソース管理をサポートするために従う必要があるガイドラインがあります。  
  
## <a name="guidelines"></a>ガイドライン  
 プロジェクトまたはエディターでは、次をソース管理をサポートするためにもを実行する必要があります。  
  
|区分|プロジェクト|エディター|説明|  
|----------|-------------|------------|-------------|  
|ファイルのプライベート コピー|x||環境では、ファイルのプライベート コピーをサポートします。 プロジェクトに参加している各ユーザーは、そのプロジェクト内のファイルの自分独自のプライベート コピーします。|  
|ANSI または Unicode の永続化|x|x|永続化コードを記述する場合は、ほとんどのソース管理プログラムは現在は Unicode をサポートしないため ANSI 形式でファイルを保持します。|  
|ファイルを列挙します。|x||プロジェクト内のすべてのファイルの特定のリストを含める必要があり、使用してファイルの一覧を列挙できる必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling)。 プロジェクトで項目名も公開する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>実装およびサポートの名前検索 (特別なファイルを含む) からその<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>実装します。|  
|テキスト形式|x|x|可能であれば、ファイルは、異なるバージョンのマージをサポートするためにテキスト形式でなければなりません。 テキスト形式ではないファイルは、ファイルの他のバージョンと後でマージすることはできません。 任意のテキスト形式は XML です。|  
|参照に基づく|x||参照に基づくプロジェクトは、ソース管理で簡単にサポートされます。 ただし、プロジェクトは、それらのファイルがディスクに存在するかどうかに関係なく、要求時にそのファイルの一覧を生成できる限り、ディレクトリ ベースのプロジェクトはソース管理でサポートもします。 ソース管理からプロジェクトを開くときに、プロジェクト ファイルは電源を切る前に、そのファイルの最初。|  
|予測可能な順序でオブジェクトとプロパティを保持します。|x|x|マージするためのアルファベット順などの予測可能な順序で、ファイルを保持します。|  
|再読み込み|x|x|ディスク上のファイルの変更、ときに、エディターは、再読み込みできなければなりません。 ソース管理に参加すると、環境は再読み込みされますデータを呼び出すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>実装します。 IVsQueryEditQuerySave を呼び出したときに、チェック アウトが発生している最も困難な再読み込み場合::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>情報を処理するとします。 ただし、再読み込みコードは、このような状況で実行できる必要があります。<br /><br /> 環境では、プロジェクト ファイルが自動的に再読み込みします。 ただし、プロジェクトを実装する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>を再読み込みをサポートするために階層がプロジェクト ファイルを入れ子になったに入れ子になった場合。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理のサポート](../../extensibility/internals/supporting-source-control.md)