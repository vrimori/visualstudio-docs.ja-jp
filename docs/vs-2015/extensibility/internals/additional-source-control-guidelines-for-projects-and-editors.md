---
title: プロジェクトとエディターの追加のソース制御のガイドライン |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c52244aa91217ae57d4265ce37a530b2e48d0e93
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770702"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>プロジェクトとエディターの追加のソース管理ガイドライン
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

プロジェクトとエディター ソース管理をサポートするために従う必要があるガイドラインを数多くあります。  
  
## <a name="guidelines"></a>ガイドライン  
 プロジェクトまたはエディターでは、次をソース管理をサポートするためにもを実行する必要があります。  
  
|区分|プロジェクト|エディター|説明|  
|----------|-------------|------------|-------------|  
|ファイルのプライベート コピー|x||環境には、ファイルのプライベート コピーがサポートされています。 これは、プロジェクトに参加している各ユーザーにそのプロジェクト内のファイルの自分独自のプライベート コピーします。|  
|ANSI または Unicode の永続化|x|x|永続化コードを記述する場合は、ほとんどのソース管理プログラムは、Unicode を現在サポートしていないため、ANSI 形式でファイルを永続化します。|  
|ファイルを列挙します。|x||プロジェクト内のすべてのファイルの特定のリストを含める必要がありを使用してファイルの一覧を列挙できる必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>または<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>(VSH_PROPID_First_Child/Next_Sibling)。 プロジェクトがを通じて項目名を公開する必要がありますもその<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A>実装とサポートの名前参照 (特殊なファイルを含む) をその<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>実装します。|  
|テキストの形式|x|x|可能であれば、ファイルは、異なるバージョンのマージをサポートするテキスト形式でなければなりません。 テキスト形式でないファイルは、ファイルの他のバージョンと後でマージすることはできません。 任意のテキスト形式には XML です。|  
|参照に基づく|x||ソース管理では、参照ベースのプロジェクトはサポートされてすぐにします。 ただし、ディレクトリ ベースのプロジェクトは、プロジェクトは、それらのファイルがディスクに存在するかどうかに関係なく、オンデマンドでそのファイルの一覧を作成できる限りもソース コントロールによってサポートされます。 ソース管理からプロジェクトを開くときにそのファイルの前に、最初、プロジェクト ファイルが終了します。|  
|予測可能な順序でオブジェクトとプロパティを保存します。|x|x|マージするためのアルファベット順などの予測可能な順序でファイルを維持します。|  
|再読み込み|x|x|ファイルがディスクに変更されると、エディターが再読み込みできる必要があります。 環境のデータを呼び出すことによって再読み込みはソース管理に参加すると、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A>実装します。 最も困難な再読み込み大文字と小文字が IVsQueryEditQuerySave を呼び出したときに、チェック アウトが発生した場合::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>情報の処理とします。 ただし、再読み込みコードは、このような状況で実行できる必要があります。<br /><br /> 環境では、プロジェクト ファイルが自動的に再読み込みします。 ただし、プロジェクトを実装する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>プロジェクト ファイルを再読み込みをサポートするために階層が入れ子になったに入れ子になった場合。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理のサポート](../../extensibility/internals/supporting-source-control.md)

