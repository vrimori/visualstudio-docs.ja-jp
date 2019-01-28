---
title: ソース コントロールの設計上の決定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f47e0bdcf5b8dd3a7c41004ce82fca9f92db509e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936829"
---
# <a name="source-control-design-decisions"></a>ソース管理のデザインの方針
ソース管理を実装する場合は、プロジェクトの次の設計に関する決定事項を検討してください。  
  
## <a name="will-information-be-shared-or-private"></a>情報は共有またはプライベートか。  
 最も重要な設計の決定を行うことは、どのような情報が共有できるとはプライベートです。 たとえば、プロジェクトのファイルの一覧を共有するが、このファイルのリスト内で一部のユーザーがファイルをプライベートにする可能性があります。 コンパイラの設定を共有することも、スタートアップ プロジェクトは通常プライベートです。 設定は、純粋な共有、上書きを共有またはプライベートのみです。 仕様では、プライベートなアイテムなど、ソリューション ユーザー オプション (.suo) ファイルはチェックされませんに[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]します。 .Suo ファイル、または特定のプライベート ファイルを作成する例などのプライベート ファイルでプライベートな情報を保管してください、。 csproj.user ファイル Visual c# または。 Visual basic の vbproj.user ファイル。  
  
 この決定は、包括的な -アイテムごとに行んだことができます。  
  
## <a name="will-the-project-include-special-files"></a>プロジェクトで特別なファイルが含まれますか。  
 もう 1 つの重要な設計上の決定は、プロジェクトの構造が特別なファイルを使用するかどうかです。 特別なファイルは、表示されるは、ソリューション エクスプ ローラーと、チェックインとチェック アウト ダイアログ ボックスにあるファイルを基になるファイルを非表示です。 特別なファイルを使用する場合は、次のガイドラインに従います。  
  
1.  プロジェクトのルート ノードを特別なファイルを関連付けないでください-これは、プロジェクト ファイル自体。 プロジェクト ファイルは、1 つのファイルである必要があります。  
  
2.  特別なファイルを追加、削除、または適切なプロジェクトで名前を変更するときに<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>ファイルは、特殊なファイルを示すフラグを設定してイベントを発生する必要があります。 これらのイベントは、応答を呼び出し、適切なプロジェクトで、環境によって呼び出される<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>メソッド。  
  
3.  プロジェクトまたはエディターを呼び出すと<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>ファイルの場合、そのファイルに関連付けられている特別なファイルに自動的にチェック アウトされていません。親ファイルと共にで特別なファイルを渡します。 環境に渡されるすべてのファイル間のリレーションシップを検出し、チェック アウトの UI で、特殊なファイルを適切に非表示にします。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [ソース管理のサポート](../../extensibility/internals/supporting-source-control.md)