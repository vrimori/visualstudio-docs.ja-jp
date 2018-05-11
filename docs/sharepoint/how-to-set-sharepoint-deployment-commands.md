---
title: '方法: SharePoint の配置コマンドを設定 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8779ba4ee4cf9803982d9849b3af7c83930d8a5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>方法: SharePoint の配置コマンドを設定する
  配置前や配置後のコマンドを設定して、展開プロセスをカスタマイズできます。 これらのコマンドは、Visual Studio からの SharePoint ソリューションをデバッグするときに、その他の展開操作の前後を実行します。  
  
### <a name="to-add-a-pre-deployment-command"></a>配置前コマンドを追加するには  
  
1.  メニュー バーで、次のように選択します。**プロジェクト**、* ProjectName ***プロパティ**です。  
  
2.  選択、 **SharePoint**タブです。  
  
3.  **配置前コマンドライン**テキスト ボックスに、この手順をカスタマイズする MS-DOS または MSBuild のコマンドを入力します。  
  
     たとえば、ディレクトリの内容の一覧を表示して、展開が完了する前に、次のように入力します。 **dir**です。  
  
### <a name="to-add-a-post-deployment-command"></a>配置後コマンドを追加するには  
  
1.  メニュー バーで、次のように選択します。**プロジェクト**、* ProjectName ***プロパティ**です。  
  
2.  選択、 **SharePoint**タブです。  
  
3.  **配置後コマンドライン**テキスト ボックスに、この手順をカスタマイズする MS-DOS または MSBuild のコマンドを入力します。  
  
     たとえば、ディレクトリの内容の一覧を表示して、展開が完了した後、次のように入力します。 **dir**です。 MSBuild 変数を使用して、ビルドのディレクトリから、アセンブリをコピーする、入力**コピー $ (targetpath) c:\DeploymentDirectory**です。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  