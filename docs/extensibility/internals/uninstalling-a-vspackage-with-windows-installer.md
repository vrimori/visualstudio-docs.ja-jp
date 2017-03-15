---
title: "Windows インストーラーで VSPackage をアンインストールします。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パッケージのアンインストール"
  - "Vspackages にあるをアンインストールします。"
  - "Vspackage をアンインストールします。"
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Windows インストーラーで VSPackage をアンインストールします。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ほとんどの場合、Windows インストーラーをアンインストールできます、VSPackage だけで「取り消し」は、VSPackage をインストールすると同じです。 カスタム動作が説明した [インストール後に実行する必要がありますコマンド](../../extensibility/internals/commands-that-must-be-run-after-installation.md) もアンインストール後に実行する必要があります。 Devenv.exe への呼び出しは、インストールとアンインストールの両方の InstallFinalize 標準的な操作の直前に発生する、ため CustomAction と InstallExecuteSequence テーブルのエントリは、どちらの場合もを使用します。  
  
> [!NOTE]
>  実行 `devenv /setup` MSI パッケージをアンインストールした後です。  
  
 一般的な規則として、Windows インストーラー パッケージにカスタム アクションを追加すると行う必要がありますそれらのアクション アンインストールし、ロールバック中にします。 など、VSPackage を自己登録するカスタム処理を追加する場合は、すぎる、登録を解除するカスタム アクションを追加する必要があります。  
  
> [!NOTE]
>  ユーザー、VSPackage をインストールしのバージョンをアンインストールすることは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 統合されているとします。 VSPackage のアンインストールが依存関係を持つコードが実行されるカスタム動作を排除することによってこのシナリオで動作することを保証できます [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
## アンインストールするときに処理の起動条件  
 LaunchConditions の標準的な操作はエラーを表示する起動条件のテーブルの行を読み取って、条件が満たされていない場合にメッセージをします。 起動条件は、システム要件を満たしている、条件を追加することで、アンインストール時に起動条件をスキップできます一般的には、一般的に使用されるため `NOT Installed`, 、起動条件の表の LaunchConditions 行にします。  
  
 別の方法は、追加する `OR Installed` がアンインストール中にでは重要でない条件を起動します。 確実に、条件は常に true のアンインストール時におよび、そのため、起動条件のエラー メッセージは表示されません。  
  
> [!NOTE]
>  `Installed` Windows インストーラでは、VSPackage が既にシステムにインストールされたことを検出したときの設定のプロパティです。  
  
## 参照  
 [Windows Installer](http://msdn.microsoft.com/ja-jp/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)