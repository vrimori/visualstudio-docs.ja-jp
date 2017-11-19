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
ms.openlocfilehash: 65c67972dddedcd05338d793883b2dcba0789d48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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
  
## <a name="see-also"></a>関連項目  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  