---
title: "ドキュメント レベルのソリューションにおけるドキュメントの保護"
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
  - "ドキュメント [Visual Studio での Office 開発], 制限されたアクセス許可"
  - "Office ドキュメント [Visual Studio での Office 開発, 制限されたアクセス許可"
  - "アクセス許可 [Visual Studio での Office 開発]"
  - "制限されたアクセス許可 [Visual Studio での Office 開発]"
  - "ブック [Visual Studio での Office 開発], 制限されたアクセス許可"
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# ドキュメント レベルのソリューションにおけるドキュメントの保護
  ドキュメント レベルのプロジェクトで、Microsoft Office Word および Microsoft Office Excel の保護機能を使用できます。  この機能は、ドキュメントの保護された部分を権限のないユーザーが変更できないようにします。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Excel の使用時は、デザイナーでブックを開いた状態で保護を有効または無効にできます。  Word の使用時は、デザイナーの外部からのみ保護を有効にできます。  実行時には、Word と Excel のいずれでもプログラムで保護を有効または無効にできます。  
  
 デザイナーで開いたドキュメントで保護が有効になっている場合、**\[ツールボックス\]** からすべてのコントロールが削除されているか、または使用不可能になっているため、**\[データ ソース\]** ウィンドウからドキュメントに何もドラッグできません。  
  
## ServerDocument と保護されたドキュメント  
 ドキュメントが保護されている場合は、ドキュメントの外部からデータ キャッシュにアクセスできません。  <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用して保護されたドキュメントにキャッシュされたデータの取得や操作を行ったり、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> クラスの他のメソッドを使用したりすることはできません。  
  
## デザイナーでの Word 文書の保護  
 Visual Studio で Word 文書を開いている間に Word 文書またはテンプレートを保護すると、デザイナーで保護を適用することはできません。  Visual Studio で開いている文書はデザイン モードになっており、保護を適用するには実行モードにする必要があります。  
  
 ただし、保護が有効になっている既存の Word 文書を使用してプロジェクトを作成する場合、デザイナーで開いている間は文書が保護されます。  文書の保護された部分を編集することはできませんが、コード エディターでコードを作成して文書を自動化することはできます。  また、Visual Studio で文書を開いている間に保護が有効になっている場合は、プロジェクトをビルドできません。  
  
 デザイナーで文書を開いている間に保護を無効にすると、文書を編集してプロジェクトをビルドできます。  デバッグ中は、デザイナーでコピーの保護を無効にすることはできません。デバッグ中に開かれている文書はデザイナーで開いた文書とは別のコピーです \(出力されたコピーは、Visual Basic では \\bin ディレクトリに、C\# では \\bin\\debug ディレクトリに格納されます\)。  
  
 デザイナーで開いた文書のコピーの保護を有効にするには、Visual Studio でプロジェクトを閉じて、プロジェクト ディレクトリにある文書のコピーを開き、保護を有効にします。  
  
## ビルド処理中の Word 文書の保護の適用  
 Visual Studio は、ビルド処理中に Word 文書およびテンプレートに対する保護の適用を開始するので、デバッグ用に文書を開いたときに保護が有効になっています。  文書は、空のパスワードで保護されています。  
  
 ビルド中に保護が有効になっているため、文書の <xref:Microsoft.Office.Tools.Word.Document.Startup> イベントに、例外やアプリケーションの動作の変更が発生する原因となるコードがある場合でも、コードは正しくデバッグされます。  文書を開いた後で保護を有効にした場合は、初期化コードに対してデバッグやテストを実行できません。  
  
## パスワードの設定  
 Visual Studio は、自動的に保護を有効にしますが、既定ではパスワードは設定されません。  パスワードで文書を保護するには、ソリューションを配置する前にパスワードを追加する必要があります。  パスワードを追加すると、承認されたユーザーが文書から保護を削除できます。パスワードがないと、保護を簡単には削除できません。  パスワードの設定の詳細については、該当する Office アプリケーションのヘルプを参照してください。  
  
## 参照  
 [方法: プログラムによって文書および文書の一部を保護する](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [Information Rights Management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)   
 [方法 : アクセス許可が制限されたドキュメントでの分離コードの実行を許可する](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  