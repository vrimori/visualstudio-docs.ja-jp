---
title: "方法: マネージ コード拡張機能をドキュメントにアタッチ |Microsoft ドキュメント"
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
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe976923c77902a4e3e42fc634a3227cadccdfc5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>方法: マネージ コード拡張機能をドキュメントにアタッチする
  カスタマイズ アセンブリは、既存の Microsoft Office Word 文書または Microsoft Office Excel ブックにアタッチできます。 文書またはブックは、Microsoft Office プロジェクトと Visual Studio での開発ツールではサポートされているすべてのファイル形式にできます。 詳細については、次を参照してください。[ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)です。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 添付するには、カスタマイズ、Word または Excel のドキュメントを使用して、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>のメソッド、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスです。 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラスは、Microsoft Office がインストールされていないコンピューターで実行するように設計されています、(コンソールまたは Windows フォーム アプリケーションの場合) などの Microsoft Office の開発に直接関連付けられていないソリューションでこのメソッドを使用することができます。  
  
> [!NOTE]  
>  カスタマイズは、コードが、指定されたドキュメントがないコントロールを要求している場合の読み込みに失敗します。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。 [i: のアタッチまたはデタッチ、Word 文書からの VSTO アセンブリ?](http://go.microsoft.com/fwlink/?LinkId=136782)です。  
  
### <a name="to-attach-managed-code-extensions-to-a-document"></a>マネージ コード拡張機能をドキュメントにアタッチするには  
  
1.  プロジェクトを必要としない Microsoft Office、コンソール アプリケーションまたは Windows フォーム プロジェクトなど、Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll および Microsoft.VisualStudio.Tools.Applications.Runtime.dll への参照を追加アセンブリ。  
  
2.  次の追加**Imports**または**を使用して**ステートメントをコード ファイルの先頭にします。  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]  
  
3.  静的なを呼び出す<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>メソッドです。  
  
     次のコード例では、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>オーバー ロードします。 このオーバー ロードは、ドキュメントの完全なパスと<xref:System.Uri>のカスタマイズをドキュメントに添付する配置マニフェストの場所を指定します。 この例では、という名前の Word 文書**worddocument1.docx など**デスクトップでは、配置マニフェストは、という名前のフォルダーに配置されていると**発行**いても、デスクトップ上。  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]  
  
4.  プロジェクトをビルドし、カスタマイズをアタッチするコンピューターでアプリケーションを実行します。 コンピューターによっては、for Office Runtime がインストールされている Visual Studio 2010 Tools が必要です。  
  
## <a name="see-also"></a>参照  
 [ServerDocument クラスを使用してサーバー上のドキュメントを管理します。](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [方法: マネージ コード拡張をドキュメントから削除](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Office ソリューションにおけるアプリケーション マニフェストと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  