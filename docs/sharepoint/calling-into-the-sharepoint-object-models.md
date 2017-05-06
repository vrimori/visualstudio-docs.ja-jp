---
title: "Calling into the SharePoint Object Models"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint development in Visual Studio, server object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Calling into the SharePoint Object Models
  Visual Studio の SharePoint ツールの拡張機能を作成するとき、特定のタスクを実行するために SharePoint の API をダイヤルする必要がある場合があります。  たとえば、SharePoint プロジェクトに対してカスタムの配置手順を作成する場合、ソリューションを配置するためのいくつかのタスクを実行する関係上、SharePoint API を呼び出す必要があります。  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] および [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] には、SharePoint ツールの拡張機能に使用できるオブジェクト モデルが 2 種類あります。サーバー オブジェクト モデルとクライアント オブジェクト モデルです。  SharePoint ツールの拡張機能からこれらのオブジェクト モデルを使用する場合、どちらのオブジェクト モデルにも長所と短所があります。  
  
 SharePoint のオブジェクト モデルの概要については、「[Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)」を参照してください。  
  
## 拡張機能プロジェクトでのクライアント オブジェクト モデルの使用  
 クライアント オブジェクト モデルは、SharePoint ツールの拡張機能を開発する場合に、プロジェクトから、他のあらゆるマネージ API と同じように使用できます。  クライアント オブジェクト モデルのアセンブリをプロジェクトから参照設定することによって、クライアント オブジェクト モデルの API を直接コードから呼び出すことができます。  
  
 ただし、SharePoint ツールの拡張機能からクライアント オブジェクト モデルを使用する場合、次の 2 つの短所があります。  
  
-   クライアント オブジェクト モデルが提供するのは、サーバー オブジェクト モデルのサブセットのみです。  クライアント オブジェクト モデルでは公開されていない SharePoint の機能を使用する必要がある場合は、サーバー オブジェクト モデルを使用する必要があります。  
  
-   SharePoint ツールの拡張機能でクライアント オブジェクト モデルを使用した場合、ほとんどのケースでは問題がないものの、クライアント オブジェクト モデルへの呼び出しがうまくいかない状況もあります。  クライアント オブジェクト モデルは、クライアント アプリケーションで、リモート サーバーまたはリモート ファームの SharePoint サイトに対して呼び出しを行うために使用されるように設計されています。  Visual Studio の SharePoint ツールは、開発コンピューターにインストールされたローカルの SharePoint 環境でのみ使用できます。  したがって、SharePoint ツールの拡張機能でクライアント オブジェクト モデルを使用する場合、呼び出し先はローカル コンピューター上のローカルの SharePoint サイトであり、これはクライアント オブジェクト モデルの意図された使用方法ではありません。  
  
 SharePoint の拡張機能でクライアント オブジェクト モデルを使用する方法を Visual Studio のツールを使用する示すチュートリアルについては、 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)" " を参照してください。  
  
## 拡張機能プロジェクトでのサーバー オブジェクト モデルの使用  
 サーバー オブジェクト モデルは、クライアント オブジェクト モデルのスーパーセットです。  サーバー オブジェクト モデルを使用した場合、[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] および [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] が公開しているすべての機能をプログラムから使用することができます。  
  
 サーバー オブジェクト モデルの API は、SharePoint ツールの拡張機能から使用することはできますが、API を直接呼び出すことはできません。  サーバー オブジェクト モデルは、.NET Framework 3.5 をターゲット フレームワークとする 64 ビット プロセスから呼び出すことができます。  一方、SharePoint ツールの拡張機能は [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] を使用し、32 ビットの Visual Studio プロセスで動作します。  そのため、SharePoint ツールの拡張機能は、SharePoint サーバー オブジェクト モデルのアセンブリを直接参照することができません。  
  
 SharePoint ツールの拡張機能でサーバー オブジェクト モデルを使用する必要がある場合は、API を呼び出すためのカスタム *SharePoint コマンド*を作成する必要があります。  SharePoint コマンドは、サーバー オブジェクト モデルを直接呼び出すことができる補助的なアセンブリで定義します。  拡張機能プロジェクトからは、<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> オブジェクトの ExecuteCommand メソッドを使用して、SharePoint コマンドを間接的に呼び出します。  
  
 SharePoint コマンドの作成および使用の詳細については、「[How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)」および「[How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)」を参照してください。  SharePoint コマンドの配置方法の詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
 SharePoint コマンドの作成方法と使用方法を説明したチュートリアルは、「[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)」および「[Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)」を参照してください。  
  
### SharePoint コマンドを実行する方法について  
 SharePoint コマンドを定義するアセンブリは、vssphost4.exe という 64 ビット ホスト プロセスに読み込まれます。  SharePoint ツール拡張機能で SharePoint コマンドを呼び出した後は、そのコマンドは 32 ビットの Visual Studio プロセス \(devenv.exe\) ではなく、vssphost4.exe で実行されます。  SharePoint コマンドを実行する方法について一部の側面を制御するには、レジストリに値を設定します。  詳細については、「[Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  
  
## 参照  
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  