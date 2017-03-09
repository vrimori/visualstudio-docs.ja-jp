---
title: "復元できない既定ファイルの関連付けがあります。 メモ: ファイルの関連付けを変更するには、このコンピューターの Administrator または Power User でなければなりません。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.0x00006A85"
  - "VS_E_RESTOREFILEASSOCS"
ms.assetid: 449c5608-83e3-4ddd-91f1-1061916995b3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 復元できない既定ファイルの関連付けがあります。 メモ: ファイルの関連付けを変更するには、このコンピューターの Administrator または Power User でなければなりません。
このエラーは、devenv コマンド ライン スイッチ \/AssociateFiles が使用され、現在のユーザーの権利ではレジストリの HKEY\_CLASSES\_ROOT セクションにアクセスできない場合に発生します。[!INCLUDE[wiprlhext](../misc/includes/wiprlhext_md.md)] で [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を実行するとき、\/AssociateFiles \(devenv.exe\) スイッチを使用するには、Administrator として devenv を実行する必要があります。  
  
### このエラーを解決するには  
  
-   管理者資格情報に変更して、操作をもう一度実行します。  
  
## 参照  
 [User Rights and Visual Studio](http://msdn.microsoft.com/ja-jp/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Devenv コマンド ライン スイッチ](../ide/reference/devenv-command-line-switches.md)