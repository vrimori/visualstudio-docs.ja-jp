---
title: "方法: ドキュメントからのマネージ コード拡張機能の削除 |Microsoft ドキュメント"
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
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 77325f725edcec41d71e5af38572f05e59c86198
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>方法: マネージ コード拡張をドキュメントから削除する
  プログラムによって、ドキュメントまたは Microsoft Office Word または Microsoft Office Excel 用ドキュメント レベルのカスタマイズの一部であるブックから、カスタマイズ アセンブリを削除することができます。 ユーザーのドキュメントを開くし、内容を表示することができますしは、ドキュメントに追加する、カスタム ユーザー インターフェイス (UI) は表示されませんが、され、コードは実行できません。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 によって提供される RemoveCustomization メソッドのいずれかを使用して、カスタマイズ アセンブリを削除することができます、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]です。 使用するメソッドは、実行時にカスタマイズを削除するかどうかによって異なります (つまり、word のカスタマイズのコードを実行して、文書または Excel ブックが開いている)、または閉じられたドキュメントまたはドキュメントのカスタマイズを削除する場合、iMicrosoft Office がインストールされていないサーバーで s。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。 [i: のアタッチまたはデタッチ、Word 文書からの VSTO アセンブリ?](http://go.microsoft.com/fwlink/?LinkId=136782)です。  
  
### <a name="to-remove-the-customization-assembly-at-run-time"></a>実行時に、カスタマイズ アセンブリを削除するには  
  
1.  呼び出し、カスタマイズ コードでは、<xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A>メソッド (Word の場合) または<xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A>メソッド (Excel)。 カスタマイズは不要になった後にのみ、このメソッドを呼び出す必要があります。  
  
     コードでこのメソッドを呼び出すのカスタマイズを使用する方法によって異なります。 たとえば、顧客は、ドキュメント自体 (カスタマイズではなく) を必要とするその他のクライアントにドキュメントを送信する準備ができるまでのカスタマイズの機能を使用して場合、は、顧客がクリックしたときに、RemoveCustomization を呼び出すいくつかの UI を提供できます。 代わりに、カスタマイズによって最初に開かれているが、カスタマイズは、顧客が直接アクセスされるその他の機能を提供しないときにデータを使用してドキュメントを作成、しを呼び出します RemoveCustomization 早く、カスタマイズドキュメントの初期化を完了します。  
  
### <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>閉じられたドキュメントまたはサーバー上のドキュメントからカスタマイズ アセンブリを削除するには  
  
1.  コンソール アプリケーションなど、Office が不要なプロジェクトまたは Windows フォーム プロジェクトでは、Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll アセンブリへの参照を追加します。  
  
2.  次の追加**Imports**または**を使用して**コード ファイルの先頭にステートメントです。  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  呼び出す、静的な<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>のメソッド、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラス、およびパラメーターのソリューションのドキュメントのパスを指定します。  
  
     次のコード例は、という名前のドキュメントから、カスタマイズを削除することを想定しています**worddocument1.docx など**デスクトップ上にあること。  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  プロジェクトをビルドし、カスタマイズを削除するコンピューターでアプリケーションを実行します。 コンピューターによっては、for Office Runtime がインストールされている Visual Studio 2010 Tools が必要です。  
  
## <a name="see-also"></a>参照  
 [ServerDocument クラスを使用してサーバー上のドキュメントを管理します。](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [方法: マネージ コード拡張機能をドキュメントにアタッチする](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  