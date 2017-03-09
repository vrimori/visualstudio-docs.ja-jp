---
title: "プロジェクト システムへの Web サービスの追加 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト システム、Web サービスの追加"
  - "Web サービス、VSPackage プロジェクト システムへの追加"
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# プロジェクト システムへの Web サービスの追加
XML Web サービスは通常SOAP プロトコル アクセス オブジェクト \(簡易\) プロトコルを使用してプロジェクト システムにプログラム情報を返す URL アドレス指定可能なリソースです。  VSPackage のプロジェクト システムに <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> インターフェイスを使用して Web サービスを統合できます。  
  
### Web サービスをプロジェクト システムに追加するには  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> のサービスによる <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> インターフェイスの呼び出し `QueryService`。  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> メソッドを呼び出します。  `NULL` として `pDiscoverySession` のパラメーターを渡す場合は検出セッションで作成され<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> のインターフェイスで後で使用できるようにセッションがキャッシュされます。  <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> への <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> のポインターを返します。  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> メソッドを呼び出します。  `pUnkWebReferenceFolder` のパラメーターとしてWeb サービス参照のフォルダーのオートメーション オブジェクトを渡します。  Visual Studio 環境ではWeb サービスが既にいるチェックします。  Web サービスがない場合環境はフォルダーとファイルに追加フォルダーの子ノードに Web サービス \(.wsdl ファイルなど\) をダウンロードして追加します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>