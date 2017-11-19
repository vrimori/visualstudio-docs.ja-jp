---
title: ".NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトを実行する変更が必要に |Microsoft ドキュメント"
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
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2a037bd26eb3caa24c86fdba63753894b0bd1af3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトの実行に必要な変更
  Office プロジェクトのターゲット フレームワークを変更するかどうか、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]後で .NET Framework の以前のバージョンから行う必要があります、開発用コンピューターとエンドユーザーのコンピューターに、ソリューションを実行できることを確認するには、次のタスクまたは。  
  
-   Visual Studio 2008 からアップグレードした場合は、プロジェクトから <xref:System.Security.SecurityTransparentAttribute> を削除します。  
  
-   実行、**クリーン**コマンドを実行または開発用コンピューター上のプロジェクトをデバッグできるように Visual Studio を実行します。  
  
-   プロジェクトの .NET Framework の必須コンポーネントを更新します。  
  
-   ターゲット フレームワークを変更する前に ClickOnce を使用してソリューションを配置した場合は、さらにエンド ユーザーがソリューションを再インストールする必要があります。  
  
 これらの各タスクの詳細については、以下の対応するセクションを参照してください。  
  
## <a name="removing-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Visual Studio 2008 からアップグレードするプロジェクトからの SecurityTransparent 属性の削除  
 Visual Studio 2008 から Office プロジェクトをアップグレードした後で、プロジェクトのターゲット フレームワークが [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更された場合は、プロジェクトから <xref:System.Security.SecurityTransparentAttribute> を削除する必要があります。 この属性は Visual Studio によって自動的に削除されません。 この属性を削除しないと、プロジェクトをコンパイルしたときにエラー メッセージが表示されます。  
  
 Visual Studio が、アップグレードされたプロジェクトのターゲット フレームワークを変更できる条件の詳細については、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]を参照してください[Office ソリューションの移行とアップグレード](../vsto/upgrading-and-migrating-office-solutions.md)です。  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>SecurityTransparentAttribute を削除するには  
  
1.  Visual Studio でプロジェクトを開き、 **ソリューション エクスプローラー**を開きます。  
  
2.  **[プロパティ]** ノード (C# の場合) または **[マイ プロジェクト]** ノード (Visual Basic の場合) の下で、AssemblyInfo コード ファイルをダブルクリックしてコード エディターで開きます。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで AssemblyInfo コード ファイルを表示するには、 **ソリューション エクスプローラー** の **[すべてのファイルの表示]** ボタンをクリックする必要があります。  
  
3.  <xref:System.Security.SecurityTransparentAttribute> を探し、ファイルから削除するか、コメント アウトします。  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="performing-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>開発用コンピューターでプロジェクトをデバッグまたは実行するための Clean コマンドの実行  
 プロジェクトのターゲット フレームワークを変更するまでに、Office プロジェクトがビルドされていた場合、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 、後で行う必要がありますか、**クリーン**コマンドし、ターゲット フレームワークを変更した後、プロジェクトをリビルドします。 場合は実行しないで、**クリーン**コマンドが表示されます、<xref:System.Runtime.InteropServices.COMException>をデバッグしたり、再ターゲットのプロジェクトを実行しようとするとします。  
  
 詳細については、**クリーン**コマンドを参照してください[Office ソリューションのビルド](../vsto/building-office-solutions.md)です。  
  
## <a name="updating-the-prerequisites-for-deployment"></a>配置する必須コンポーネントの更新  
 Office プロジェクトのターゲットを変更するときに[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]以降、する必要がありますもの更新プログラムの対応する .NET Framework の前提条件、**の前提条件** ダイアログ ボックス。 そうしない場合は、ClickOnce 配置または InstallShield Limited Edition プロジェクトが以前のバージョンの .NET Framework をチェックし、インストールします。  
  
 エンドユーザーのコンピューターに展開の前提条件の更新に関する詳細については、次を参照してください。[する方法: インストールの前提条件エンドユーザーのコンピューターに Office ソリューションを実行する](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)です。  
  
## <a name="reinstalling-solutions-on-end-user-computers"></a>エンド ユーザーのコンピューターでのソリューションの再インストール  
 ClickOnce を使用して .NET Framework 3.5 を対象とする Office ソリューションを配置してから、プロジェクトの対象を [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更した場合、エンド ユーザーはソリューションをアンインストールし、再発行後のソリューションを再インストールする必要があります。 対象が変更されたソリューションを再発行し、エンド ユーザーのコンピューター上でソリューションが更新された場合は、エンド ユーザーが更新されたソリューションを実行したときに <xref:System.Runtime.InteropServices.COMException> が発生します。  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework 4 以降への Office ソリューションの移行](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  