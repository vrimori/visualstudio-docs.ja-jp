---
title: "方法: SharePoint の配置コマンドを設定 |Microsoft ドキュメント"
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
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d5692195f340ce347df0bc6f8ad2d60225f24e6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>方法: SharePoint の配置コマンドを設定する
  配置前や配置後のコマンドを設定して、展開プロセスをカスタマイズできます。 これらのコマンドは、Visual Studio からの SharePoint ソリューションをデバッグするときに、その他の展開操作の前後を実行します。  
  
### <a name="to-add-a-pre-deployment-command"></a>配置前コマンドを追加するには  
  
1.  メニュー バーで、 **[プロジェクト]**、[ *ProjectName***のプロパティ]**」を参照してください。  
  
2.  選択、 **SharePoint**タブです。  
  
3.  **配置前コマンドライン**テキスト ボックスに、この手順をカスタマイズする MS-DOS または MSBuild のコマンドを入力します。  
  
     たとえば、ディレクトリの内容の一覧を表示して、展開が完了する前に、次のように入力します。 **dir**です。  
  
### <a name="to-add-a-post-deployment-command"></a>配置後コマンドを追加するには  
  
1.  メニュー バーで、 **[プロジェクト]**、[ *ProjectName***のプロパティ]**」を参照してください。  
  
2.  選択、 **SharePoint**タブです。  
  
3.  **配置後コマンドライン**テキスト ボックスに、この手順をカスタマイズする MS-DOS または MSBuild のコマンドを入力します。  
  
     たとえば、ディレクトリの内容の一覧を表示して、展開が完了した後、次のように入力します。 **dir**です。 MSBuild 変数を使用して、ビルドのディレクトリから、アセンブリをコピーする、入力**コピー $ (targetpath) c:\DeploymentDirectory**です。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  