---
title: ソース コントロールの設計に関する決定事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0385d5feb7baf7fe60e253616c8db0f326932e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-design-decisions"></a>ソース コントロールの設計に関する決定事項
ソース管理を実装する場合は、プロジェクトの次の設計に関する決定事項を考慮してください。  
  
## <a name="will-information-be-shared-or-private"></a>情報は共有またはプライベートになりますか。  
 最も重要な設計上の決定を行うことはどのような情報が共有できるとはプライベートです。 などのプロジェクトのファイルの一覧を共有するが、このファイルのリスト内で一部のユーザーするプライベート ファイルがあります。 コンパイラの設定を共有することもスタートアップ プロジェクトには一般にプライベートです。 設定は、純粋な共有、共有、上書きを使ってまたは純粋なプライベートです。 仕様では、プライベートなアイテムのソリューション ユーザー オプション (.suo) ファイルなどはチェックされませんに[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]です。 .Suo ファイルを作成するなど、特定のプライベート ファイルなどのプライベート ファイルにプライベートな情報を格納することを確認する、です。 Visual c# csproj.user ファイルまたはです。 Visual basic の vbproj.user ファイル。  
  
 この決定は、包括的ながあり、項目間の単位で行われたことができます。  
  
## <a name="will-the-project-include-special-files"></a>プロジェクトには特別なファイルが含まれますか。  
 他の重要な設計の意思決定は、プロジェクトの構造が特別なファイルを使用するかどうかです。 特別なファイルは、表示されるは、ソリューション エクスプ ローラーと、チェックインおよびチェック アウト ダイアログ ボックスにあるファイルを基になる隠しファイルです。 特別なファイルを使用する場合は、次のガイドラインに従います。  
  
1.  プロジェクトのルート ノードに特別なファイルを関連付けない-は、プロジェクト ファイル自体です。 プロジェクト ファイルは、1 つのファイルである必要があります。  
  
2.  特別なファイルを追加、削除、またはプロジェクトでは、適切な名前を変更するときに<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>は特殊なファイルを示すフラグを設定してイベントを発生する必要があります。 これらのイベントは、適切な呼び出しプロジェクトへの応答で、環境によって呼び出される<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>メソッドです。  
  
3.  プロジェクトまたはエディターが呼び出されると<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>ファイルの場合、そのファイルに関連付けられている特別なファイルに自動的にチェック アウトされていません。親ファイルと共にで特別なファイルを渡します。 環境内で渡されるすべてのファイルの間のリレーションシップを検出し、チェック アウト UI で特別なファイルを適切に表示しません。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [ソース管理のサポート](../../extensibility/internals/supporting-source-control.md)