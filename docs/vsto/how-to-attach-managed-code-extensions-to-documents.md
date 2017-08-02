---
title: "方法: マネージ コード拡張機能をドキュメントにアタッチする"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ドキュメント [Visual Studio での Office 開発], マネージ コード拡張機能"
  - "マネージ コード拡張機能 [Visual Studio での Office 開発], アタッチ"
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 方法: マネージ コード拡張機能をドキュメントにアタッチする
  カスタマイズ アセンブリを、既存の Microsoft Office Word 文書または Microsoft Office Excel ブックにアタッチできます。  ドキュメントまたはブックは、Visual StudioのMicrosoft Officeプロジェクトと開発ツールでサポートされている任意のファイル形式を指定できます。  詳細については、「[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)」を参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 カスタマイズを Word 文書または Excel ドキュメントにアタッチするには、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスの <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> メソッドを使用します。  <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスは Microsoft Office がインストールされていないコンピューターで実行することを意図されているため、このメソッドは、Microsoft Office 開発に直接関連していないソリューション \(コンソール アプリケーションや Windows フォーム アプリケーションなど\) で使用できます。  
  
> [!NOTE]  
>  指定されたドキュメントに、コードで予期されているコントロールが含まれていないと、カスタマイズは読み込みに失敗します。  
  
 ![ビデオへのリンク](~/data-tools/media/playvideo.gif "ビデオへのリンク") 関連のビデオ デモについては、「[How Do I: Attach or Detach a VSTO Assembly from a Word Document? \(操作方法: Word 文書から VSTO アセンブリをアタッチまたはデタッチする\)](http://go.microsoft.com/fwlink/?LinkId=136782)」を参照してください。  
  
### マネージ コード拡張機能をドキュメントに追加するには  
  
1.  Microsoft Officeを、コンソール アプリケーションやWindowsフォーム プロジェクトなど、必要としないプロジェクトでは、Microsoft.VisualStudio.Tools.Applications.ServerDocument.dllおよびMicrosoft.VisualStudio.Tools.Applications.Runtime.dllのアセンブリへの参照を追加します。  
  
2.  次の **Imports** ステートメントまたは **using** ステートメントをコード ファイルの先頭に追加します。  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#4)]  
  
3.  静的な <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> メソッドを呼び出します。  
  
     次のコード例では、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> オーバーロードを使用します。  このオーバーロードは、ドキュメントの完全パスと、ドキュメントに追加するカスタマイズの配置マニフェストの場所を指定する <xref:System.Uri> を使用します。  この例では、**WordDocument1.docx** という Word 文書がデスクトップ上に存在し、配置マニフェストがデスクトップ上の **Publish** というフォルダーにあることを前提としています。  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#3)]  
  
4.  カスタマイズをアタッチするコンピューターで、プロジェクトをビルドしてアプリケーションを実行します。  コンピューターにがインストールされているOffice RuntimeのVisual Studio 2010 Toolsをインストールする必要があります。  
  
## 参照  
 [ServerDocument クラスによるサーバー上のドキュメントの管理](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [方法: マネージ コード拡張をドキュメントから削除する](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Office ソリューションにおけるアプリケーション マニフェストと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  