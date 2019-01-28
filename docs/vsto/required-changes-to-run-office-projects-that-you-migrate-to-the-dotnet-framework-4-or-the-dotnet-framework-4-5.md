---
title: .NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトの実行に必要な変更
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7577ad079b354821a65f741dc8578f94ce383f2e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863527"
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 または .NET Framework 4.5 に移行する Office プロジェクトの実行に必要な変更
  Office プロジェクトのターゲット フレームワークを変更するかどうか、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または後で、.NET Framework の以前のバージョンから行う必要があります、開発用コンピューターとエンドユーザーのコンピューターにソリューションを実行できるようにするには、次のタスク。  
  
- Visual Studio 2008 からアップグレードした場合は、プロジェクトから <xref:System.Security.SecurityTransparentAttribute> を削除します。  
  
- 実行、**クリーン**コマンドを Visual Studio が実行または開発用コンピューターでプロジェクトをデバッグできるようにします。  
  
- プロジェクトの .NET Framework の必須コンポーネントを更新します。  
  
- ターゲット フレームワークを変更する前に ClickOnce を使用してソリューションを配置した場合は、さらにエンド ユーザーがソリューションを再インストールする必要があります。  
  
  これらの各タスクの詳細については、以下の対応するセクションを参照してください。  
  
## <a name="remove-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Visual Studio 2008 からアップグレードしたプロジェクトからの SecurityTransparent 属性を削除します。  
 Visual Studio 2008 から Office プロジェクトをアップグレードした後で、プロジェクトのターゲット フレームワークが [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更された場合は、プロジェクトから <xref:System.Security.SecurityTransparentAttribute> を削除する必要があります。 この属性は Visual Studio によって自動的に削除されません。 この属性を削除しないと、プロジェクトをコンパイルしたときにエラー メッセージが表示されます。  
  
 Visual Studio がアップグレードされたプロジェクトのターゲット フレームワークを変更できる条件の詳細については、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]を参照してください[アップグレードし、Office ソリューションの移行](../vsto/upgrading-and-migrating-office-solutions.md)します。  
  
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
  
## <a name="perform-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>開発用コンピューターでプロジェクトを実行またはデバッグのための clean コマンドを実行します。  
 Office プロジェクトのプロジェクトのターゲット フレームワークを変更するまで作成した場合、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]またはを実行する必要があります、**クリーン**コマンドを実行し、ターゲット フレームワークを変更した後、プロジェクトをリビルドします。 場合実行しないで、**クリーン**コマンドが表示されます、<xref:System.Runtime.InteropServices.COMException>再ターゲットのプロジェクトを実行またはデバッグしようとするとします。  
  
 詳細については、**クリーン**コマンドを参照してください[ビルドの Office ソリューション](../vsto/building-office-solutions.md)します。  
  
## <a name="update-the-prerequisites-for-deployment"></a>更新の展開の前提条件  
 Office プロジェクトの再ターゲット[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]、後で更新することも必要がありますも、対応する .NET Framework の前提条件、**の前提条件** ダイアログ ボックス。 そうしない場合は、ClickOnce 配置または InstallShield Limited Edition プロジェクトが以前のバージョンの .NET Framework をチェックし、インストールします。  
  
 エンドユーザーのコンピューターに展開の前提条件の更新に関する詳細については、次を参照してください。[方法。Office ソリューションを実行するためにエンド ユーザー コンピューターの前提条件をインストール](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)します。  
  
## <a name="reinstall-solutions-on-end-user-computers"></a>エンドユーザーのコンピューターにソリューションを再インストールします。  
 ClickOnce を使用して .NET Framework 3.5 を対象とする Office ソリューションを配置してから、プロジェクトの対象を [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更した場合、エンド ユーザーはソリューションをアンインストールし、再発行後のソリューションを再インストールする必要があります。 対象が変更されたソリューションを再発行するエンドユーザーのコンピューターで、ソリューションが更新された場合は、エンドユーザーが表示されます、<xref:System.Runtime.InteropServices.COMException>更新したソリューションを実行したときにします。  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework 4 またはそれ以降の Office ソリューションを移行します。](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
