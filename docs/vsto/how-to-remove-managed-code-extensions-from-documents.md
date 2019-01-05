---
title: '方法: ドキュメントからのマネージ コード拡張機能を削除します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2057fe53a571bccf04373636f83aaedecebfd4ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964774"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>方法: ドキュメントからのマネージ コード拡張機能を削除します。
  プログラムによって、ドキュメントまたは Microsoft Office Word または Microsoft Office Excel のドキュメント レベルのカスタマイズの一部であるブックからカスタマイズ アセンブリを削除することができます。 ユーザーのドキュメントを開くし、内容を表示できますし、ドキュメントに追加する、カスタム ユーザー インターフェイス (UI) は表示されませんと、コードは実行できません。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 いずれかを使用して、カスタマイズ アセンブリを削除することができます、`RemoveCustomization`によって提供されるメソッド、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。 使用する方法は、実行時にカスタマイズを削除するかどうかによって異なります (つまり、カスタマイズ、Word でコードを実行して文書または Excel ブックが開いている)、閉じられたドキュメントまたはドキュメントからカスタマイズを削除する場合、またはその iMicrosoft Office がインストールされていないサーバーで s。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください[How Do i:。アタッチまたは Word 文書から VSTO アセンブリをデタッチしますか。](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
## <a name="to-remove-the-customization-assembly-at-runtime"></a>実行時に、カスタマイズ アセンブリを削除するには  
  
1.  カスタマイズ コードを呼び出す、 <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> (Word) のメソッドまたは<xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A>メソッド (for Excel)。 カスタマイズが不要になった後にのみ、このメソッドを呼び出す必要があります。  
  
     コードでこのメソッドを呼び出す独自のカスタマイズの使用方法によって異なります。 たとえば、顧客は、ドキュメント自体 (カスタマイズではなく) を必要とするその他のクライアントにドキュメントを送信する準備ができるまでのカスタマイズの機能を使用して場合、を呼び出すいくつかの UI を指定できます`RemoveCustomization`顧客がそれをクリックしたとき。 また場合は、カスタマイズを初めて開くが、カスタマイズは顧客が直接アクセスされるその他の機能を提供しない場合に、ドキュメントにデータを設定します、し、呼び出すことができます RemoveCustomization 早く、カスタマイズドキュメントの初期化を終了します。  
  
## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>閉じられたドキュメントまたはサーバー上のドキュメントからカスタマイズ アセンブリを削除するには  
  
1.  参照を追加するコンソール アプリケーションまたは Windows フォーム プロジェクトなど、Microsoft Office を必要としないプロジェクトで、 *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll*アセンブリ。  
  
2.  次の追加**Imports**または**を使用して**ステートメントをコード ファイルの先頭にします。  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  呼び出す静的<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>のメソッド、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラス、およびパラメーターのソリューションのドキュメントのパスを指定します。  
  
     次のコード例は、という名前のドキュメントからカスタマイズを削除することを想定しています*worddocument1.docx など*デスクトップです。  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  プロジェクトをビルドし、カスタマイズを削除するコンピューターでアプリケーションを実行します。 コンピューターには、Visual Studio 2010 Tools for Office ランタイムがインストールされている必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ServerDocument クラスを使用してサーバー上のドキュメントを管理します。](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [方法: マネージ コード拡張をドキュメントにアタッチします。](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
