---
title: "アプリケーション マニフェストおよび配置マニフェスト Office ソリューションの |Microsoft ドキュメント"
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
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
ms.assetid: 4e9abc7c-ef9f-4cb2-a7a9-c95c5f4a1fb7
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 822be7f0e6e79f600331197c60ed48ea84cde200
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Office ソリューションにおけるアプリケーション マニフェストと配置マニフェスト
  アプリケーション マニフェストは、Office ソリューションがアセンブリを特定して更新する際に使用する情報を提供する XML ファイルです。 アプリケーション マニフェストは配置マニフェストと共に使用できます。配置マニフェストは、サーバーに保存されている XML ファイルです。最新バージョンのアプリケーション マニフェストとアセンブリを特定するために必要な情報を提供します。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="manifest-structure-for-office-solutions"></a>Office ソリューションのマニフェストの構造  
 Visual Studio で Office 開発ツールを使用して作成された Microsoft Office ソリューションの場合、すべてのマニフェストは、標準の ClickOnce スキーマに基づいています。 Office ソリューションを配置すると、ドキュメントレベルと VSTO アドイン プロジェクトの両方のアプリケーション マニフェストは、ClickOnce キャッシュに保存されます。 配置マニフェストは、クライアント コンピューターにコピーされません。  
  
 Office プロジェクトのアプリケーション マニフェストと配置マニフェストの内容について詳しくは、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md) 」と「 [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md)」をご覧ください。  
  
## <a name="creating-application-and-deployment-manifests"></a>アプリケーション マニフェストと配置マニフェストの作成  
 アプリケーション マニフェストは、ビルド プロセスの一環として自動的に作成されます。 ドキュメントレベルのプロジェクトをビルドするたびに、配置マニフェストの場所はカスタム ドキュメント プロパティとしてドキュメントに埋め込まれます。 VSTO アドインの場合、配置マニフェストの場所はレジストリに格納されます。  
  
 詳細については、**発行ウィザード**を参照してください[ClickOnce を使用して Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)です。  
  
 方法の詳細については、Office ソリューションで作業をマニフェストを参照してください。 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [設計と、Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)   
 [ClickOnce 配置マニフェス](/visualstudio/deployment/clickonce-deployment-manifest)  
  
  