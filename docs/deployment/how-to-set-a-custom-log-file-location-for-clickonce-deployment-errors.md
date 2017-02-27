---
title: "方法 : ClickOnce 配置エラー用にカスタム ログ ファイルの場所を設定する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 配置, エラーのログ"
  - "ClickOnce 配置, トラブルシューティング"
  - "トラブルシューティング (ClickOnce 配置を)"
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : ClickOnce 配置エラー用にカスタム ログ ファイルの場所を設定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は、すべての配置に対してアクティべーション ログ ファイルを保持しています。  これらのログには、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置のインストールと初期化に関連するすべてのエラーが記録されます。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は、既定で、配置がアクティブ化されるたびにログ ファイルを 1 つずつ作成します。  これらのログ ファイルは、Temporary Internet Files フォルダーに格納されます。  アクティベーション エラーが発生すると配置のログ ファイルがユーザーに表示され、ユーザーは表示されたエラー ダイアログ ボックスで **\[詳細\]** をクリックします。  
  
 特定のクライアントに対してこの動作を変更するには、レジストリ エディター \(**regedit.exe**\) を使用してカスタム ログ ファイルのパスを設定します。  この場合、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は、すべての配置のアクティベーションの成功と失敗を 1 つのログ ファイルに記録します。  
  
> [!CAUTION]
>  レジストリ エディターで不適切な操作を行うと、重大な問題が発生して、オペレーティング システムの再インストールが必要になる場合があります。  問題が発生する可能性のあることを十分に認識したうえで利用してください。  
  
> [!NOTE]
>  ログ ファイルは、大きくなりすぎないように、ときどき切り詰めるか削除する必要があります。  
  
 単一のクライアントに対してカスタム ログ ファイルの場所を設定する方法を、次の手順で説明します。  
  
### カスタム ログ ファイルの場所を設定するには  
  
1.  **Regedit.exe** を起動します。  
  
2.  `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` ノードまで移動します。  
  
3.  `LogFilePath` 文字列値を、使用するカスタム ログの場所の完全パスとファイル名に設定します。  
  
     この場所は、ユーザーが書き込みアクセス権を持つディレクトリ内であることが必要です。  たとえば、Windows Vista では、次のフォルダー構造を作成し、`LogFilePath` を C:\\Users\\\<ユーザー名\>\\Documents\\Logs\\ClickOnce\\installation.log に設定します。  
  
## 参照  
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)