---
title: ".NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトの実行に必要な変更 | Microsoft Docs"
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
  - "Office プロジェクト [Visual Studio での Office 開発], 移行 (.NET Framework 4 への)"
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# .NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトの実行に必要な変更
  Office プロジェクトのターゲット フレームワークを旧バージョンの .NET Framework から [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、ソリューションを開発用コンピューターとエンド ユーザーのコンピューターで実行できるようにするため、次のタスクを実行する必要があります。  
  
-   Visual Studio 2008 からアップグレードした場合は、プロジェクトから <xref:System.Security.SecurityTransparentAttribute> を削除します。  
  
-   開発用コンピューターでプロジェクトを実行またはデバッグできるように、Visual Studio で **Clean** コマンドを実行します。  
  
-   プロジェクトの .NET Framework の必須コンポーネントを更新します。  
  
-   ターゲット フレームワークを変更する前に ClickOnce を使用してソリューションを配置した場合は、さらにエンド ユーザーがソリューションを再インストールする必要があります。  
  
 これらの各タスクの詳細については、以下の対応するセクションを参照してください。  
  
## Visual Studio 2008 からアップグレードするプロジェクトからの SecurityTransparent 属性の削除  
 Visual Studio 2008 から Office プロジェクトをアップグレードした後で、プロジェクトのターゲット フレームワークが [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更された場合は、プロジェクトから <xref:System.Security.SecurityTransparentAttribute> を削除する必要があります。 この属性は Visual Studio によって自動的に削除されません。 この属性を削除しないと、プロジェクトをコンパイルしたときにエラー メッセージが表示されます。  
  
 Visual Studio がアップグレードされたプロジェクトのターゲット フレームワークを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] に変更できる条件の詳細については、「[Office ソリューションのアップグレードと移行](../vsto/upgrading-and-migrating-office-solutions.md)」を参照してください。  
  
#### SecurityTransparentAttribute を削除するには  
  
1.  Visual Studio でプロジェクトを開き、**ソリューション エクスプローラー**を開きます。  
  
2.  **\[プロパティ\]** ノード \(C\# の場合\) または **\[マイ プロジェクト\]** ノード \(Visual Basic の場合\) の下で、AssemblyInfo コード ファイルをダブルクリックしてコード エディターで開きます。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで AssemblyInfo コード ファイルを表示するには、**ソリューション エクスプローラー**の **\[すべてのファイルの表示\]** をクリックする必要があります。  
  
3.  <xref:System.Security.SecurityTransparentAttribute> を探し、ファイルから削除するか、コメント アウトします。  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## 開発用コンピューターでプロジェクトをデバッグまたは実行するための Clean コマンドの実行  
 Office プロジェクトをビルドした後でプロジェクトのターゲット フレームワークを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、ターゲット フレームワークを変更した後、**Clean** コマンドを実行してからプロジェクトをビルドし直す必要があります。  **Clean** コマンドを実行しないと、対象が変更されたプロジェクトをデバッグまたは実行しようとしたときに <xref:System.Runtime.InteropServices.COMException> が発生します。  
  
 **Clean** コマンドの詳細については、「[Office ソリューションのビルド](../vsto/building-office-solutions.md)」を参照してください。  
  
## 配置する必須コンポーネントの更新  
 Office プロジェクトの対象を [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、**\[必須コンポーネント\]** ダイアログ ボックスで .NET Framework の対応する必須コンポーネントを更新する必要があります。  そうしない場合は、ClickOnce 配置または InstallShield Limited Edition プロジェクトが以前のバージョンの .NET Framework をチェックし、インストールします。  
  
 エンド ユーザーのコンピューターに配置する必須コンポーネントの更新の詳細については、[方法: Office ソリューションを実行するための必須コンポーネントをエンド ユーザーのコンピューターにインストールする](http://msdn.microsoft.com/ja-jp/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)を参照してください。  
  
## エンド ユーザーのコンピューターでのソリューションの再インストール  
 ClickOnce を使用して .NET Framework 3.5 を対象とする Office ソリューションを配置してから、プロジェクトの対象を [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更した場合、エンド ユーザーはソリューションをアンインストールし、再発行後のソリューションを再インストールする必要があります。  対象が変更されたソリューションを再発行し、エンド ユーザーのコンピューター上でソリューションが更新された場合は、エンド ユーザーが更新されたソリューションを実行したときに <xref:System.Runtime.InteropServices.COMException> が発生します。  
  
## 参照  
 [.NET Framework 4 以降への Office ソリューションの移行](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  