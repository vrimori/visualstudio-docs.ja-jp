---
title: "方法: マネージ コード拡張をドキュメントから削除する"
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
  - "マネージ コード拡張機能 [Visual Studio での Office 開発], 削除"
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 方法: マネージ コード拡張をドキュメントから削除する
  Microsoft Office Word または Microsoft Office Excel のドキュメント レベルのカスタマイズの一部であるドキュメントまたはブックから、カスタマイズ アセンブリをプログラムによって削除することができます。  その後、ドキュメントを開き、内容を表示できますが、ドキュメントに追加されたどのカスタム ユーザー インターフェイス \(UI\) も表示されません。また、コードも実行されません。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 カスタマイズ アセンブリを削除するには、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって提供されるいずれかの RemoveCustomization メソッドを使用します。  使用するメソッドは、実行時にカスタマイズを削除する \(Word 文書または Excel ブックが開いているときにカスタマイズでコードを実行する\) か、閉じられたドキュメントまたは Microsoft Office がインストールされていないサーバー上にあるドキュメントからカスタマイズを削除するかによって異なります。  
  
 ![ビデオへのリンク](~/data-tools/media/playvideo.gif "ビデオへのリンク") 関連のビデオ デモについては、「[How Do I: Attach or Detach a VSTO Assembly from a Word Document? \(操作方法: Word 文書から VSTO アセンブリをアタッチまたはデタッチする\)](http://go.microsoft.com/fwlink/?LinkId=136782)」を参照してください。  
  
### 実行時にカスタマイズ アセンブリを削除するには  
  
1.  カスタマイズ コードで、<xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> メソッド \(Word の場合\) または <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> メソッド \(Excel の場合\) を呼び出します。  このメソッドは、カスタマイズの必要がなくなった場合にのみ呼び出す必要があります。  
  
     コード内でこのメソッドを呼び出す場所は、カスタマイズが使用される状況によって異なります。  たとえば、\(カスタマイズではなく\) 文書自体を必要とする他のクライアントに文書を送信する準備が整うまで顧客がカスタマイズの機能を使用する場合は、顧客がクリックしたときに RemoveCustomization を呼び出す UI を提供できます。  または、文書が最初に開かれたときにカスタマイズによって文書のデータが設定され、顧客が直接アクセスする他の機能はカスタマイズでは提供されない場合、カスタマイズが文書の初期化を完了した直後に RemoveCustomization を呼び出すことができます。  
  
### 閉じられたドキュメントまたはサーバー上にあるドキュメントからカスタマイズ アセンブリを削除するには  
  
1.  Microsoft Officeを、コンソール アプリケーションやWindowsフォーム プロジェクトなど、必要としないプロジェクトでは、Microsoft.VisualStudio.Tools.Applications.ServerDocument.dllアセンブリへの参照を追加します。  
  
2.  次の **Imports** ステートメントまたは **using** ステートメントをコード ファイルの先頭に追加します。  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#1)]  
  
3.  <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスの静的な <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> メソッドを呼び出し、ソリューション ドキュメントのパスをパラメーターに指定します。  
  
     次のコード例では、デスクトップ上にある **WordDocument1.docx** という名前のドキュメントからカスタマイズを削除することを前提としています。  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#2)]  
  
4.  カスタマイズを削除するコンピューターで、プロジェクトをビルドしてアプリケーションを実行します。  コンピューターにがインストールされているOffice RuntimeのVisual Studio 2010 Toolsをインストールする必要があります。  
  
## 参照  
 [ServerDocument クラスによるサーバー上のドキュメントの管理](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [方法: マネージ コード拡張機能をドキュメントにアタッチする](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  