---
title: "SharePoint オブジェクト モデルの呼び出し |Microsoft ドキュメント"
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
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: cbb1b8f573c6dd28280e30fd5602dff2dc30ae02
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="calling-into-the-sharepoint-object-models"></a>SharePoint オブジェクト モデルの呼び出し
  Visual Studio で SharePoint ツールの拡張機能を作成するときに、特定のタスクを実行する SharePoint Api を呼び出す必要があります。 たとえば、SharePoint プロジェクト用のカスタム配置手順を作成する場合はいくつかのソリューションを展開するタスクを実行する SharePoint Api を呼び出す必要があります。  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]および[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]SharePoint ツール拡張機能で使用できる 2 つの別のオブジェクト モデルを提供します。 サーバー オブジェクト モデルとクライアント オブジェクト モデルです。 オブジェクトが各モデルに利点と欠点があります SharePoint ツール拡張機能のコンテキストでします。  
  
 SharePoint オブジェクト モデルの概要については、次を参照してください。[プログラミング モデルの SharePoint ツール拡張機能の概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)です。  
  
## <a name="using-the-client-object-model-in-extension-projects"></a>拡張機能プロジェクトでのクライアント オブジェクト モデルの使用  
 SharePoint ツール拡張機能を開発する場合は、マネージ Api の他の任意のセットと同様に、プロジェクトのクライアント オブジェクト モデルを使用することができます。 クライアント オブジェクト モデルのアセンブリへの参照を追加するには、プロジェクトにして、コードから直接クライアント オブジェクト モデルの Api を呼び出すことができます。  
  
 ただし、クライアント オブジェクト モデルでは、SharePoint ツール拡張機能のコンテキストで 2 つの欠点があります。  
  
-   クライアント オブジェクト モデルでは、サーバー オブジェクト モデルのサブセットのみを提供します。 クライアント オブジェクト モデルで公開されていない SharePoint 機能を使用した場合は、サーバー オブジェクト モデルを使用する必要があります。  
  
-   SharePoint ツール拡張機能で、クライアント オブジェクト モデルを使用すると、ほとんどの場合が動作するはずですが、場所としてクライアント オブジェクト モデルへの呼び出しは正常に動作しない一部のシナリオが発生する可能性があります。 クライアント オブジェクト モデルは、リモート サーバーまたはファームで SharePoint サイトへの呼び出しをクライアント アプリケーションで使用するよう設計されています。 Visual Studio での SharePoint ツールは、開発用コンピューターにローカル SharePoint のインストールでのみ動作します。 したがって、クライアント オブジェクト モデルを SharePoint ツール拡張機能を使用する場合を呼び出して、SharePoint サイトにないクライアント オブジェクト モデルの設計方法を使用するには、ローカル コンピューターでします。  
  
 Visual Studio での SharePoint ツールの拡張機能に、クライアント オブジェクト モデルを使用する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: サーバー エクスプ ローラー拡張機能では、SharePoint クライアント オブジェクト モデルを呼び出す](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)です。  
  
## <a name="using-the-server-object-model-in-extension-projects"></a>拡張機能プロジェクトで、サーバー オブジェクト モデルの使用  
 サーバー オブジェクト モデルは、クライアント オブジェクト モデルのスーパー セットです。 サーバー オブジェクト モデルを使用する場合は、すべての機能を使用することができますを[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]と[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]プログラムを公開します。  
  
 SharePoint ツール拡張機能は、サーバー オブジェクト モデルで Api を使用することができますが、直接、Api を呼び出すことはできません。 サーバー オブジェクト モデルは、.NET Framework 3.5 を対象と 64 ビット プロセスからのみ呼び出すことができます。 ただし、SharePoint ツール拡張機能が必要、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Visual Studio の 32 ビット プロセスで実行するとします。 これは SharePoint ツール拡張機能が SharePoint サーバー オブジェクト モデル内のアセンブリを直接参照することを防ぎます。  
  
 を SharePoint ツール拡張機能で、サーバー オブジェクト モデルを使用する場合は、カスタムを作成する必要があります*SharePoint コマンド*API を呼び出すためです。 SharePoint コマンドは、サーバー オブジェクト モデルを直接呼び出すことができるセカンダリ アセンブリで定義します。 拡張機能のプロジェクトでしていない SharePoint コマンドを直接呼び出すの ExecuteCommand メソッドを使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>オブジェクト。  
  
 作成と SharePoint コマンドの使用に関する詳細については、次を参照してください。[する方法: SharePoint コマンドを作成する](../sharepoint/how-to-create-a-sharepoint-command.md)と[する方法: SharePoint コマンドを実行](../sharepoint/how-to-execute-a-sharepoint-command.md)です。 SharePoint コマンドを展開する方法については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
 作成し、SharePoint のコマンドを使用する方法を示すチュートリアルについては、次を参照してください[チュートリアル: SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)と[チュートリアル: サーバー エクスプ ローラー表示 Web に拡張します。パーツ](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)です。  
  
### <a name="understanding-how-sharepoint-commands-are-executed"></a>Understanding のどの SharePoint コマンドを実行します。  
 SharePoint コマンドを定義するアセンブリは vssphost4.exe をという名前の 64 ビット ホスト プロセスに読み込まれます。 SharePoint ツール拡張機能での SharePoint コマンドを呼び出すと、コマンドは、32 ビット Visual Studio プロセス (devenv.exe) ではなく vssphost4.exe によって実行されます。 レジストリ内の値を設定して SharePoint コマンドを実行する方法の一部の側面を制御できます。 詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能のデバッグ](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>参照  
 [方法: SharePoint コマンドを作成します。](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [方法: SharePoint コマンドを実行](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [SharePoint ツール拡張機能のプログラミング モデルの概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  