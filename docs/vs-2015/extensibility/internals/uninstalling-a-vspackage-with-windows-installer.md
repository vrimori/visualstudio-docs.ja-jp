---
title: Windows インストーラーによる VSPackage のアンインストール |Microsoft Docs
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
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24931206b6956d77414a2885758645db71e3cfff
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539400"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows インストーラーによる VSPackage のアンインストール
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Windows インストーラー VSPackage でのアンインストール](https://docs.microsoft.com/visualstudio/extensibility/internals/uninstalling-a-vspackage-with-windows-installer)します。  
  
ほとんどの場合、Windows インストーラーをアンインストールできます VSPackage だけで、VSPackage のインストールを行った「取り消し」。 カスタム アクションは、後ほど[コマンドをする必要がありますが実行後にインストール](../../extensibility/internals/commands-that-must-be-run-after-installation.md)もアンインストール後に実行する必要があります。 Devenv.exe への呼び出しは、InstallFinalize の標準的なアクションのインストールおよびアンインストールの両方の直前に発生する、CustomAction と InstallExecuteSequence テーブル エントリはどちらの場合もを提供します。  
  
> [!NOTE]
>  実行`devenv /setup`MSI パッケージをアンインストールした後。  
  
 一般的な規則として、Windows インストーラー パッケージにカスタム アクションを追加する場合は、行う必要がありますこれらのアクション アンインストールし、ロールバック中にします。 たとえば、VSPackage を自己登録するカスタム アクションを追加する場合は、すぎる、登録を解除するカスタム アクションを追加する必要があります。  
  
> [!NOTE]
>  ユーザーが、VSPackage をインストールしのバージョンをアンインストールすることは[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]統合されているとします。 VSPackage のアンインストールがで依存関係を持つコードを実行するカスタム動作を排除することでこのシナリオで動作することを確認できます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>アンインストールするときに起動条件の処理  
 LaunchConditions 標準アクションには、エラーを表示する起動条件のテーブルの行が読み取られます。 条件が満たされていない場合にメッセージをします。 起動条件のように、条件を追加することで、アンインストール中に起動条件をスキップできます一般に、システム要件を満たしているは一般的に使用されるため`NOT Installed`LaunchConditions の起動条件のテーブルの行にします。  
  
 別の方法は、追加する`OR Installed`がアンインストール中にでは重要でない条件を起動します。 確実に条件は必ず true アンインストール中にし、そのため、起動条件のエラー メッセージは表示されません。  
  
> [!NOTE]
>  `Installed` Windows インストーラーが、VSPackage がシステムに既にインストールされていることを検出したときに設定するプロパティです。  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラー](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)

