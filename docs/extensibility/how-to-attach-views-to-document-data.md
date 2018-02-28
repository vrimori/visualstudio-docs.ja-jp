---
title: "方法: 添付データを文書化するビュー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bcbb3e6b475a9dcd22d012073d3197013da337c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-views-to-document-data"></a>方法: 添付ドキュメント データへのビュー
新しいドキュメント ビューを使っている場合は、既存のドキュメント データ オブジェクトにアタッチすることができます。  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>既存のドキュメント データ オブジェクトにビューをアタッチすることができるかどうかを決定するには  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> を実装します。  
  
2.  実装で`IVsEditorFactory::CreateEditorInstance`、呼び出す`QueryInterface`IDE を呼び出すときに既存のドキュメント データ オブジェクトに対して、`CreateEditorInstance`実装します。  
  
     呼び出す`QueryInterface`で指定されている、既存のドキュメント データ オブジェクトを調べることができます、`punkDocDataExisting`パラメーター。  
  
     クエリを実行する必要があります、正確なインターフェイスはただしに、手順 4 で説明したよう、ドキュメントを開いて、エディターによって異なります。  
  
3.  既存のドキュメント データ オブジェクトに適切なインターフェイスが見つからない場合は、ドキュメント データ オブジェクトが、エディターでは互換性がないことを示す、エディターにはエラー コードを返します。  
  
     IDE の実装で<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>、メッセージ ボックスに通知する、ドキュメントが別のエディターで開かれているし、閉じることを確認します。  
  
4.  このドキュメントを閉じると場合、Visual Studio は 2 回目に、エディター ファクトリを呼び出して、します。 この呼び出しで、`DocDataExisting`パラメーターが NULL です。 エディター ファクトリの実装は、独自のエディターでドキュメント データ オブジェクトを開くことができます。  
  
    > [!NOTE]
    >  既存のドキュメント データ オブジェクトを使用できるかどうかを判断するのに使用することも、インターフェイスの実装に関する知識をプライベートで実際にポインターをキャスト[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]プライベートな実装のクラスです。 たとえば、すべての標準的なエディターを実装して`IVsPersistFileFormat`から継承される<xref:Microsoft.VisualStudio.OLE.Interop.IPersist>です。 したがって、呼び出すことができます`QueryInterface`の<xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>、既存のドキュメント データ オブジェクトのクラス ID と一致実装のクラス ID、し、ドキュメントのデータ オブジェクトを操作することができます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 Visual Studio での実装を呼び出すと、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッド、戻るのポインターに渡すには、既存のドキュメント データ オブジェクト、`punkDocDataExisting`パラメーターを 1 つが存在する場合。 返されるドキュメント データ オブジェクトを調べる`punkDocDataExisting`ドキュメント データ オブジェクトが、このトピックの手順の手順 4 で注で説明したように、エディターの該当するかを判断します。 これは、適切なかどうかは、エディター ファクトリで説明したように、データの 2 つ目のビューを提供する必要があります[複数ドキュメントのビューをサポートする](../extensibility/supporting-multiple-document-views.md)です。 それ以外の場合は、適切なエラー メッセージが表示にする必要があります。  
  
## <a name="see-also"></a>参照  
 [複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)   
 [カスタム エディターでのドキュメント データとドキュメント ビュー](../extensibility/document-data-and-document-view-in-custom-editors.md)