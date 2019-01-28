---
title: SharePoint オブジェクト モデルの呼び出し |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd6e8d1bbd2f880a3e3c4c7fab4b292a2c7bd6d0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875668"
---
# <a name="call-into-the-sharepoint-object-models"></a>SharePoint オブジェクト モデルを呼び出す
  Visual Studio での SharePoint ツールの拡張機能を作成するときに、特定のタスクを実行する SharePoint Api を呼び出す必要があります。 たとえば、SharePoint プロジェクトのカスタム配置手順を作成する場合はいくつかのソリューションを展開するタスクを実行する SharePoint Api を呼び出す必要があります。  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] SharePoint ツール拡張機能で使用できる 2 つの別のオブジェクト モデルを提供します。 サーバー オブジェクト モデルとクライアント オブジェクト モデルです。 各オブジェクト モデルは、SharePoint ツール拡張機能のコンテキストで利点と欠点が。  
  
 SharePoint オブジェクト モデルの概要については、次を参照してください。[ツールの拡張機能を SharePoint のプログラミング モデルの概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)します。  
  
## <a name="use-the-client-object-model-in-extension-projects"></a>拡張機能プロジェクトでのクライアント オブジェクト モデルを使用します。
 SharePoint ツールの拡張機能を開発する際に、その他のマネージ Api セットに似たプロジェクトでクライアント オブジェクト モデルを使用することができます。 クライアント オブジェクト モデルのアセンブリへの参照を追加するには、プロジェクトにして、コードから直接クライアント オブジェクト モデルでの Api を呼び出すことができます。  
  
 ただし、クライアント オブジェクト モデルでは、SharePoint ツール拡張機能のコンテキストで 2 つの欠点があります。  
  
- クライアント オブジェクト モデルでは、サーバー オブジェクト モデルのサブセットのみを提供します。 クライアント オブジェクト モデルで公開されていない SharePoint 機能を使用した場合は、サーバー オブジェクト モデルを使用する必要があります。  
  
- SharePoint ツール拡張機能で、クライアント オブジェクト モデルを使用すると、ほとんどの場合が動作するはずですが、場所クライアント オブジェクト モデルへの呼び出しは正常に動作しない一部のシナリオが発生する可能性があります。 クライアント オブジェクト モデルは、リモート サーバーまたはファームで SharePoint サイトへの呼び出しをクライアント アプリケーションで使用する設計されています。 Visual Studio での SharePoint ツールは、開発用コンピューターでローカルの SharePoint インストールでのみ動作します。 そのため、クライアント オブジェクト モデルを SharePoint ツール拡張機能を使用する場合、SharePoint サイトにで呼び出していないクライアント オブジェクト モデルの設計方法を使用するには、ローカル コンピューター。  
  
  Visual Studio の SharePoint ツールの拡張機能で、クライアント オブジェクト モデルを使用する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル。サーバー エクスプ ローラー拡張機能では、SharePoint クライアント オブジェクト モデルを呼び出す](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)します。  
  
## <a name="use-the-server-object-model-in-extension-projects"></a>拡張機能プロジェクトで、サーバー オブジェクト モデルを使用します。
 サーバー オブジェクト モデルでは、クライアント オブジェクト モデルのスーパー セットです。 サーバー オブジェクト モデルを使用する場合は、すべての機能を使用することができますを[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]と[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]プログラムで公開します。  

 SharePoint ツール拡張機能は、サーバー オブジェクト モデルで Api を使用することができますが、直接、Api を呼び出すことはできません。 サーバー オブジェクト モデルを対象とする .NET Framework 3.5、64 ビット プロセスからのみ呼び出すことができます。 ただし、SharePoint ツール拡張機能が必要、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Visual Studio の 32 ビット プロセスで実行するとします。 これは SharePoint ツール拡張機能が、SharePoint サーバー オブジェクト モデル内のアセンブリを直接参照することを防ぎます。  
  
 SharePoint ツール拡張機能で、サーバー オブジェクト モデルを使用する場合は、カスタムを作成する必要があります*SharePoint コマンド*API を呼び出します。 SharePoint コマンドを定義するにはセカンダリ アセンブリに、サーバー オブジェクト モデルを直接呼び出すことができます。 拡張プロジェクトでない SharePoint コマンドを直接呼び出すことの ExecuteCommand メソッドを使用して、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>オブジェクト。  
  
 作成して、SharePoint コマンドの使用の詳細については、次を参照してください。[方法。SharePoint コマンドを作成する](../sharepoint/how-to-create-a-sharepoint-command.md)と[方法。SharePoint コマンドを実行](../sharepoint/how-to-execute-a-sharepoint-command.md)します。 SharePoint コマンドを展開する方法については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能を展開](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
 作成して SharePoint コマンドを使用する方法を説明するチュートリアルでは、次を参照してください。[チュートリアル。SharePoint プロジェクトのカスタム配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)と[チュートリアル。Web パーツを表示するサーバー エクスプ ローラーを拡張](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)します。  
  
### <a name="understand-how-sharepoint-commands-are-executed"></a>SharePoint コマンドを実行する方法を理解します。
 SharePoint コマンドを定義するアセンブリはという名前の 64 ビット ホスト プロセスで読み込まれる*vssphost4.exe*します。 コマンドを実行後、SharePoint ツール拡張機能の SharePoint コマンドを呼び出すと、 *vssphost4.exe* Visual Studio の 32 ビット プロセスではなく (*devenv.exe*)。 レジストリの値を設定して SharePoint コマンドを実行する方法の一部の側面を制御できます。 詳細については、次を参照してください。 [Visual Studio の SharePoint ツールの拡張機能をデバッグ](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)します。  
  
## <a name="see-also"></a>関連項目
 [方法: SharePoint コマンドを作成します。](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [方法: SharePoint コマンドを実行します。](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [ツールの拡張機能を SharePoint のプログラミング モデルの概要](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
