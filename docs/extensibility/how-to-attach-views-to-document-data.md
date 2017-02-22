---
title: "方法: データを文書化するビューのアタッチ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] - カスタム ビューをドキュメント データに添付します。"
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: データを文書化するビューのアタッチ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

新しいドキュメント ビューの場合は、既存のドキュメント データ オブジェクトにアタッチすることができます。  
  
### 既存のドキュメント データ オブジェクトにビューをアタッチするにはかどうかを判断するには  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> を実装します。  
  
2.  実装で `IVsEditorFactory::CreateEditorInstance`, 、呼び出す `QueryInterface` 既存ドキュメント データ オブジェクト、IDE を呼び出すときに、 `CreateEditorInstance` 実装します。  
  
     呼び出す `QueryInterface` で指定された既存のドキュメント データ オブジェクトを調べることができます、 `punkDocDataExisting` パラメーター。  
  
     クエリを実行する必要があります、正確なインターフェイスはただしに、手順 4 で説明したようは、ドキュメントを開いて、エディターによって異なります。  
  
3.  既存のドキュメント データ オブジェクトに適切なインターフェイスが見つからない場合は、ドキュメントのデータ オブジェクトのエディターで互換性がないことを示すエディターにエラー コードを返します。  
  
     IDE の実装で <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, 、メッセージ ボックスに通知する、ドキュメントが別のエディターで開かれているし、閉じることを確認します。  
  
4.  このドキュメントを閉じる場合、Visual Studio は 2 回エディター ファクトリを呼び出して、します。 この呼び出しで、 `DocDataExisting` パラメーターが NULL です。 エディター ファクトリの実装は、独自のエディターでドキュメントのデータ オブジェクトを開くことができます。  
  
    > [!NOTE]
    >  既存のドキュメント データ オブジェクトを使用できるかどうかを確認するのに使用することもプライベート インターフェイスの実装に関する実際へのポインターをキャストして [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] プライベートな実装のクラスです。 たとえば、すべての標準エディター実装 `IVsPersistFileFormat`, から継承される <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>します。 このため、呼び出すことができます `QueryInterface` の <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, 、および既存のドキュメント データ オブジェクトのクラス ID が、実装と一致するかどうかのクラス ID、し、ドキュメントのデータ オブジェクトを操作することができます。  
  
## 信頼性の高いプログラミング  
 Visual Studio での実装を呼び出すと、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> メソッドに渡すポインター内の既存のドキュメント データ オブジェクトを `punkDocDataExisting` が存在する場合のパラメーターです。 返されるドキュメントのデータ オブジェクトを調べる `punkDocDataExisting` ドキュメント データ オブジェクトがこのトピックの手順の手順 4 での注で説明したように、エディターの該当するかを判断します。 これは、適切なかどうかは、エディター ファクトリで説明したように、データの 2 つ目のビューを提供する必要があります [複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)します。 それ以外の場合は、適切なエラー メッセージが表示にする必要があります。  
  
## 参照  
 [複数のドキュメント ビューをサポートします。](../extensibility/supporting-multiple-document-views.md)   
 [ドキュメント データとカスタム エディターでドキュメント ビュー](../extensibility/document-data-and-document-view-in-custom-editors.md)