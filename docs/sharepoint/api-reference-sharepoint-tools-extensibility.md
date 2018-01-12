---
title: "API リファレンス (SharePoint ツールの拡張性) |Microsoft ドキュメント"
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
helpviewer_keywords: SharePoint development in Visual Studio, reference for project and tools extensibility
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a44f54e80ec3b4c91198666ed7066e6308d3e602
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="api-reference-sharepoint-tools-extensibility"></a>API リファレンス (SharePoint ツールの拡張性)
  このセクションでは、Visual Studio の SharePoint ツールを拡張するための API リファレンス ドキュメントを示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 <xref:Microsoft.VisualStudio.SharePoint>  
 SharePoint プロジェクト システムを拡張するのに使用する型があります。 たとえば、組み込みの SharePoint プロジェクトやプロジェクト項目を拡張できるほか、独自のプロジェクト項目を作成することもできます。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Commands>  
 カスタムの作成に使用できる型を含む*SharePoint コマンド*です。 SharePoint コマンドは、SharePoint のサーバー オブジェクト モデルに対する呼び出しを SharePoint ツールの拡張機能から行うメソッドです。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Deployment>  
 SharePoint プロジェクトの配置プロセスを拡張する際に使用する型があります。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Explorer>  
 使用する SharePoint ノードを拡張する型を含む**サーバー エクスプ ローラー**またはノードの独自の型を定義します。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>  
 組み込みに関する情報の取得に使用できる型を含む**サーバー エクスプ ローラー**リスト、フィールド、またはコンテンツの種類を表すノードなどの SharePoint サイト上の個々 のコンポーネントを表すノードです。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Features>  
 SharePoint プロジェクトのフィーチャーの定義にアクセスするために使用する型があります。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Packages>  
 SharePoint プロジェクトのパッケージ定義にアクセスするために使用する型があります。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>  
 リモート SharePoint サイトに配置する SharePoint アプリの認証とそれらのアプリとの通信に使用する型があります。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>  
 リモート SharePoint サイトに配置する SharePoint アプリ用の SharePoint リモート コマンドを作成するために使用する型があります。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Tasks>  
 Visual Studio で SharePoint プロジェクト、Office アプリ、SharePoint アプリのパッケージ化とデバッグ用のビルド タスクとして使用する型があります。 この API は、Office および SharePoint インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。  
  
 <xref:Microsoft.VisualStudio.SharePoint.Validation>  
 SharePoint プロジェクトの機能およびパッケージ検証動作をカスタマイズするために使用する型があります。  
  
## <a name="see-also"></a>参照  
 [リファレンス &#40;です。SharePoint ツールの機能拡張 &#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [ツールの拡張機能を SharePoint のプログラミング モデルの概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [SharePoint プロジェクト システムの拡張](../sharepoint/extending-the-sharepoint-project-system.md)   
 [サーバー エクスプ ローラーで SharePoint 接続 ノードを拡張します。](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [SharePoint の拡張のパッケージ化と配置](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [SharePoint オブジェクト モデルの呼び出し](../sharepoint/calling-into-the-sharepoint-object-models.md)  
  
  