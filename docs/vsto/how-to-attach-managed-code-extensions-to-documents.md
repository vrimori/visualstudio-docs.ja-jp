---
title: '方法: マネージ コード拡張機能をドキュメントにアタッチします。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: aa7eda6dfed28ceebb9b400568463cc689993f1e
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646894"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>方法: マネージ コード拡張機能をドキュメントにアタッチします。
  カスタマイズ アセンブリは、既存の Microsoft Office Word 文書または Microsoft Office Excel ブックにアタッチできます。 文書またはブックは、Microsoft Office プロジェクトと Visual Studio での開発ツールでサポートされている任意のファイル形式にできます。 詳細については、次を参照してください。[のドキュメント レベル カスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)します。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Word または Excel ドキュメントにカスタマイズをアタッチするには使用、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>のメソッド、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラス。 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスが Microsoft Office がインストールされていないコンピューターで実行するため、このメソッドは、(コンソールまたは Windows フォーム アプリケーションの場合) などの Microsoft Office の開発に直接関連していないソリューションで使用できます。  
  
> [!NOTE]  
>  カスタマイズは、コードが、指定されたドキュメントがないコントロールを必要とする場合の読み込みに失敗します。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください[How do i:アタッチまたは Word 文書から VSTO アセンブリをデタッチしますか。](http://go.microsoft.com/fwlink/?LinkId=136782)  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>マネージ コード拡張機能をドキュメントにアタッチするには  
  
1.  参照を追加するコンソール アプリケーションまたは Windows フォーム プロジェクトなど、Microsoft Office を必要としないプロジェクトで、 *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll*と*Microsoft.VisualStudio.Tools.Applications.Runtime.dll*アセンブリ。  
  
2.  次の追加**Imports**または**を使用して**ステートメントをコード ファイルの先頭にします。  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  呼び出す静的<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>メソッド。  
  
     次のコード例では、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>オーバー ロードします。 このオーバー ロードは、ドキュメントの完全なパスと<xref:System.Uri>ドキュメントにアタッチするカスタマイズの配置マニフェストの場所を指定します。 この例では、という名前の Word 文書**worddocument1.docx など**、デスクトップ上にあるという名前のフォルダーに配置マニフェストがあると**発行**もデスクトップ上にあります。  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  プロジェクトをビルドし、カスタマイズをアタッチするコンピューターでアプリケーションを実行します。 コンピューターでは、Office ランタイムがインストールされている Visual Studio 2010 Tools が必要です。  
  
## <a name="see-also"></a>関連項目  
 [ServerDocument クラスを使用してサーバー上のドキュメントを管理します。](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [方法: ドキュメントからのマネージ コード拡張機能を削除します。](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Office ソリューションにおけるアプリケーションと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  