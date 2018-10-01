---
title: プロジェクトのアップグレード |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 74ec29dbc4aae393d9ee09fa6a9de273369ce7cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47535691"
---
# <a name="upgrading-projects"></a>プロジェクトのアップグレード
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロジェクト アップグレード](https://docs.microsoft.com/visualstudio/extensibility/internals/upgrading-projects)します。  
  
プロジェクト モデルの 1 つのバージョンから変更[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]へ必要があります、新しいバージョンで実行できるようにプロジェクトおよびソリューションをアップグレードします。 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]独自のプロジェクトのアップグレードのサポートを実装するために使用できるインターフェイスを提供します。  
  
## <a name="upgrade-strategies"></a>アップグレードの戦略  
 アップグレードをサポートするには、プロジェクト システムの実装が定義し、アップグレードの戦略を実装する必要があります。 戦略を決定するのには、サイド バイ サイド (SxS) のバックアップ、バックアップのコピー、またはその両方をサポートするために選択できます。  
  
-   SxS バックアップでは、プロジェクトがアップグレード インプレースでは、たとえば、適切なファイル名サフィックスを追加".old"必要があるファイルのみをコピーを意味します。  
  
-   コピー バックアップでは、プロジェクトが、ユーザーが指定したバックアップの場所へのすべてのプロジェクト項目をコピーすることを意味します。 元のプロジェクトの場所に関連するファイルは、アップグレードします。  
  
## <a name="how-upgrade-works"></a>アップグレードする方法の動作  
 以前のバージョンで作成されたソリューションと[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]はソリューション ファイルにアップグレードする必要があるかどうかは決まりますを IDE の確認、新しいバージョンで開かれます。 アップグレードが必要な場合、**アップグレード ウィザード**がアップグレードのプロセスを順を追ってに自動的に起動します。  
  
 ソリューションでは、アップグレードする必要があります、そのアップグレードの戦略の場合は、各プロジェクト ファクトリを照会します。 戦略は、プロジェクト ファクトリが、コピーまたは SxS のバックアップをサポートしているかどうかを判断します。 情報に送信、**アップグレード ウィザード**バックアップに必要な情報を収集およびユーザーに適切なオプションを表示します。  
  
### <a name="multi-project-solutions"></a>マルチ プロジェクト ソリューション  
 ソリューションには、複数のプロジェクトが含まれています。 プロジェクト ファクトリがアップグレード戦略をネゴシエートする必要がありますのみ SxS のバックアップをサポートする C++ プロジェクトと Web プロジェクトのみバックアップ コピーをサポートするなど、アップグレードの戦略が異なる場合。  
  
 ソリューションのクエリの各プロジェクト ファクトリ<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>します。 呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>グローバル プロジェクト ファイルのアップグレードに必要なかどうかを参照して、サポートされているアップグレードの戦略を決定します。 **アップグレード ウィザード**呼び出されます。  
  
 ユーザーが、ウィザードを完了した後<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>は実際のアップグレードを実行するには、各プロジェクト ファクトリに対して呼び出されます。 IVsProjectUpgradeViaFactory メソッドを提供するバックアップを容易に、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>アップグレード プロセスの詳細を記録するサービス。 このサービスをキャッシュすることはできません。  
  
 関連するすべてのグローバル ファイルを更新した後は、各プロジェクト ファクトリは、プロジェクトをインスタンス化を選択できます。 プロジェクトの実装をサポートする必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>すべての関連するプロジェクト項目のアップグレードにはメソッドが呼び出されます。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>メソッドが SVsUpgradeLogger サービスを提供できません。 このサービスを呼び出すことによって取得できる<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>します。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>編集する前にファイルを編集することができ、保存する前に保存できるかどうかにチェックするサービス。 これにより、バックアップと、アップグレードの実装がソース管理下にあるプロジェクト ファイル、権限の不足などのファイルを処理します。  
  
 使用して、<xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>バックアップのすべてのフェーズ中にサービスし、アップグレード、アップグレード処理の成否に関する情報を提供します。  
  
 バックアップして、プロジェクトのアップグレードの詳細については、コメントを参照して IVsProjectUpgrade の vsshell2.idl でします。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト](../../extensibility/internals/projects.md)   
 [カスタム プロジェクトのアップグレード](../../misc/upgrading-custom-projects.md)   
 [プロジェクト項目のアップグレード](../../misc/upgrading-project-items.md)

