---
title: ドキュメント レベルのソリューションでドキュメントの保護
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: b6894aa05adf55945383cb3c2e28b8c5fdebdc16
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908854"
---
# <a name="document-protection-in-document-level-solutions"></a>ドキュメント レベルのソリューションでドキュメントの保護
  Microsoft Office Word および Microsoft Office Excel のドキュメント レベルのプロジェクトでの保護機能を使用することができます。 これらの機能は、ドキュメントの保護された部分を変更する権限のないユーザーをブロックします。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Excel を使用して、ブックがデザイナーで開いている間での保護にオンとオフをできます。 Word を使用して、デザイナーの外側でのみ保護を有効にできます。 、実行時に、有効または、Word と Excel の両方のプログラムによる保護を無効にできます。  
  
 すべてのコントロールを削除は、デザイナーで開いているドキュメントのドキュメントの保護が有効の場合、**ツールボックス**無効、またはから何をドラッグすることはできません、**データソース**ドキュメント ウィンドウです。  
  
## <a name="serverdocument-and-protected-documents"></a>ServerDocument と保護されたドキュメント  
 ドキュメントが保護されている場合、データ キャッシュをドキュメントの外部からアクセスできません。 使用することはできません、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>を取得または保護されたドキュメントにキャッシュされているデータを操作するクラスまたはその他の方法を使用して、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>クラス。  
  
## <a name="word-document-protection-in-the-designer"></a>デザイナーで Word 文書の保護  
 Visual Studio で開いているときに、Word 文書またはテンプレートを保護を追加する場合は、デザイナーでの保護の適用を開始できません。 Visual Studio で開いているしする必要があります実行モードにする保護の適用を開始する前に、ドキュメントがデザイン モード。  
  
 ただし、保護を有効になっている既存の Word 文書を使用するプロジェクトを作成する場合は、ドキュメントがデザイナーで開いている間保護されています。 ドキュメントの保護された部分を編集することはできませんが、まだコードを記述できるコード エディターでドキュメントを自動化します。 ことはできませんプロジェクトをビルドする場合は、文書が Visual Studio で開いているときに、保護を有効にします。  
  
 ドキュメントを編集して、プロジェクトをビルドできるように、ドキュメントがデザイナーで開いているときに、保護を無効にできます。 デバッグする場合、デザイナー内のコピーの保護を無効にすることはできません。デバッグ中に開かれるドキュメントがデザイナーで開いてから別のコピー (に出力のコピーが格納されている、 *\bin* Visual basic では、ディレクトリ、 *\bin\debug* (C#) またはディレクトリ)。  
  
 Visual Studio でプロジェクトを閉じて、プロジェクト ディレクトリ内にあるドキュメントのコピーを開き、保護を有効にして、デザイナーで開かれているドキュメントのコピーの保護を有効にすることができます。  
  
## <a name="enforce-word-document-protection-on-build"></a>ビルド時に Word 文書の保護を適用します。  
 デバッグ用のドキュメントを開いたときに、保護が有効にするために、visual Studio は、ビルド プロセス中に、Word 文書やテンプレートの保護の適用を開始します。 ドキュメントは、空のパスワードで保護されます。  
  
 保護が有効になっているビルド時にこれをドキュメント内のコードがある場合<xref:Microsoft.Office.Tools.Word.Document.Startup>イベント、アプリケーションの動作を変更したり、例外が発生する可能性がありますが、このコードをできるデバッグ正しくします。 ドキュメントが開かれた後に保護を有効にした場合の初期化コードをデバッグまたはテストできません。  
  
## <a name="setting-the-password"></a>パスワードの設定  
 Visual Studio は自動的に保護しますが、既定ではパスワードにはありません。 パスワードを文書を保護する場合は、ソリューションを配置する前に追加する必要があります。 承認されたユーザーがドキュメントの保護を解除するパスワードを追加することができます。パスワードのない保護を簡単に削除することはできません。 パスワードの設定について詳しくは、特定の Office アプリケーションのヘルプを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって文書および文書の一部を保護します。](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [Information rights management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)   
 [方法: 制限されたアクセス許可を持つドキュメントの背後で実行するコードを許可します。](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [設計および Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)  
