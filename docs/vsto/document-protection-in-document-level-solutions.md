---
title: "ドキュメント レベルのソリューションでの保護を文書化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
ms.assetid: a25472ad-03f0-4804-9d19-e5ff71340d49
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ceecad94d3f9bb910f47484e5deab0f20876a0d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="document-protection-in-document-level-solutions"></a>ドキュメント レベルのソリューションにおけるドキュメントの保護
  ドキュメント レベルのプロジェクトでは、Microsoft Office Word および Microsoft Office Excel の保護機能を使用することができます。 これらの機能は、ドキュメントの保護された部分を変更する権限のないユーザーをブロックします。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Excel を使用して、ブックがデザイナーで開いているときにで保護を有効または無効にことができます。 Word を使用して、デザイナーの外側でのみ保護を有効にできます。 実行時に、有効にするにまたは Word と Excel の両方のプログラムによる保護を無効にできます。  
  
 すべてのコントロールが削除された文書の保護が有効では、デザイナーで開いているドキュメントの場合、**ツールボックス**無効、またはから何もをドラッグすることはできませんし、**データソース**ドキュメント ウィンドウです。  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument と保護されたドキュメント  
 ドキュメントが保護されている場合、データ キャッシュをドキュメントの外部からアクセスできません。 使用することはできません、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>を取得または保護されたドキュメントでキャッシュされているデータを操作するクラスまたはその他のメソッドを使用して、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>クラスです。  
  
## <a name="word-document-protection-in-the-designer"></a>デザイナーで Word 文書の保護  
 Visual Studio で開いているときは、Word 文書またはテンプレートに保護を追加する場合は、デザイナーでの保護の適用を開始できません。 実行しなければならないことにモード保護の適用を開始する前に、Visual Studio で開いている間に、ドキュメントはデザイン モードです。  
  
 ただし、保護を有効になっている既存の Word 文書を使用するプロジェクトを作成する場合は、ドキュメントがデザイナーで開いているときに保護されます。 ドキュメントの保護された部分を編集することはできませんが、作成することもコード、コード エディターでドキュメントを自動化します。 できませんプロジェクトをビルドする場合は、文書が Visual Studio で開いているときに、保護を有効にします。  
  
 ドキュメントを編集して、プロジェクトをビルドできるように、ドキュメントがデザイナーで開いている間に、保護を無効にできます。 デバッグしている間は、デザイナー内のコピーの保護を無効にすることはできません。デバッグ中に開かれるドキュメントは、(Visual basic の場合は、\bin ディレクトリと c# の \bin\debug ディレクトリで、出力のコピーを格納します)、デザイナーで、1 つが開いてから別のコピーです。  
  
 Visual Studio でプロジェクトを閉じて、プロジェクト ディレクトリ内にあるドキュメントのコピーを開き、保護を有効にして、デザイナーで開かれているドキュメントのコピーの保護を有効にすることができます。  
  
## <a name="enforcing-word-document-protection-on-build"></a>ビルド時に Word 文書の保護を適用します。  
 デバッグ用のドキュメントを開いたときに、保護が有効にするために、visual Studio は、ビルド処理中に Word 文書やテンプレートの保護の適用を開始します。 ドキュメントは、空のパスワードで保護されます。  
  
 保護が有効になっているビルド時にこれをドキュメント内のコードがある場合<xref:Microsoft.Office.Tools.Word.Document.Startup>イベント、アプリケーションの動作を変更したり、例外が発生する可能性がある、このコードは、デバッグ対象正しくです。 ドキュメントが開かれた後に保護を有効にした場合の初期化コードをデバッグまたはテストできません。  
  
## <a name="setting-the-password"></a>パスワードの設定  
 Visual Studio は自動的に保護を有効しますが、既定ではパスワードが用意されていません。 パスワードを保持する文書を保護する場合は、ソリューションを配置する前に追加する必要があります。 承認されたユーザーがドキュメントの保護を解除するパスワードを追加することができます。パスワードのない保護を簡単に削除することはできません。 パスワードの設定の詳細については、特定の Office アプリケーションのヘルプを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって文書および文書の一部を保護します。](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [Information Rights Management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)   
 [方法: アクセス許可の制限のドキュメントの背後に実行するようにコードを許可します。](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)  
  
  