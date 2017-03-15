---
title: "方法: ClickOnce 配置用の詳細ログ ファイルを指定する | Microsoft Docs"
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
  - "ClickOnce 配置, ログ記録"
  - "ログ, ClickOnce 配置"
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法: ClickOnce 配置用の詳細ログ ファイルを指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] は、すべての配置に対してアクティビティ ログ ファイルを保持しています。  これらのログには、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置のインストール、初期化、更新、およびアンインストールに関連する詳細が記録されています。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] によってこれらのログ ファイルに書き込まれる情報の詳細度を上げるには、レジストリ エディター \(**regedit.exe**\) を使用して詳細出力レベルを指定します。  
  
> [!CAUTION]
>  レジストリ エディターで不適切な操作を行うと、重大な問題が発生して、オペレーティング システムの再インストールが必要になる場合があります。  問題が発生する可能性のあることを十分に認識したうえで利用してください。  
  
 現在のユーザーの [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ログ ファイルの詳細出力レベルを指定する方法を次の手順で説明します。  詳細出力レベルを下げるには、このレジストリ値を削除します。  
  
### 詳細ログ ファイルを指定するには  
  
1.  **Regedit.exe** を起動します。  
  
2.  `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` ノードまで移動します。  
  
3.  必要に応じて、`LogVerbosityLevel` という名前の新しい文字列値を作成します。  
  
4.  `LogVerbosityLevel` の値を `1` に設定します。  
  
## 参照  
 [ClickOnce 配置のトラブルシューティング](../deployment/troubleshooting-clickonce-deployments.md)