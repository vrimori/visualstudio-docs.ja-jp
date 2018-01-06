---
title: "Windows インストーラーで VSPackage をアンインストールする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ee8ad89e02dfa8aebbb39a9d7ebe523ad01bb7e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows インストーラーで VSPackage をアンインストールします。
ほとんどの場合、Windows インストーラーをアンインストールできます VSPackage だけで「元に戻す」は、VSPackage をインストールします。 カスタム アクションは、後ほど[コマンドする必要がある実行後にインストール](../../extensibility/internals/commands-that-must-be-run-after-installation.md)もアンインストール後に実行する必要があります。 Devenv.exe への呼び出しは、インストールとアンインストールの両方の installfinalize が標準的な操作の直前に発生する、CustomAction と InstallExecuteSequence テーブルのエントリはどちらの場合に機能します。  
  
> [!NOTE]
>  実行`devenv /setup`MSI パッケージをアンインストールした後にします。  
  
 一般的な規則として場合は、Windows インストーラー パッケージにカスタム アクションを追加する必要がありますを処理するそれらのアクション アンインストールし、ロールバック中に。 たとえば、VSPackage を自己登録するカスタム アクションを追加する場合は、すぎる、登録を解除するカスタム アクションを追加する必要があります。  
  
> [!NOTE]
>  ユーザー、VSPackage をインストールしのバージョンをアンインストールすることは[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合されているとします。 依存関係を持つコードを実行するカスタム動作を排除することでこのシナリオでは、VSPackage のアンインストールが動作することを確認できます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>処理の起動条件でアンインストールするとき  
 LaunchConditions 標準アクション エラーを表示する起動条件のテーブルの行の読み取りを条件が満たされていない場合にメッセージをします。 起動条件はシステム要件を満たしていることを条件には、追加することで、アンインストール中に起動条件をスキップできます一般的に使用されるため、通常`NOT Installed`、起動条件の表の LaunchConditions 行にします。  
  
 代わりに、追加し`OR Installed`重要ではないアンインストール中に条件を起動します。 条件が必ず true アンインストール中にして、そのため、起動条件のエラー メッセージは表示されませんされるようにします。  
  
> [!NOTE]
>  `Installed`Windows インストーラーが、VSPackage が既にシステムにインストールされたことを検出したときに設定するプロパティです。  
  
## <a name="see-also"></a>参照  
 [Windows インストーラー](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)