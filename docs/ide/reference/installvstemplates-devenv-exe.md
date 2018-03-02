---
title: "devenv.exe の InstallVSTemplates スイッチ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /InstallVSTemplates switch
- /InstallVSTemplates Devenv switch
- InstallVSTemplates switch
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 529979caa801ace8dd649cf1614f2eeb27ca070b
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="installvstemplates-devenvexe"></a>/InstallVSTemplates (devenv.exe)

/InstallVSTemplates スイッチは、\<*Visual Studio インストール パス*>\Common7\IDE\ProjectTemplates\ または \<*Visual Studio インストール パス*>\Common7\IDE\ItemTemplates\ にあるプロジェクトや項目テンプレートを登録して、**[新しいプロジェクト]** ダイアログ ボックスおよび **[新しい項目の追加]** ダイアログ ボックスからアクセスできるようにします。

> [!WARNING]
> このスイッチは、Visual Studio パートナーの開発用にのみサポートされています。 [/Setup (devenv.exe)](../../ide/reference/setup-devenv-exe.md) スイッチおよび [/InstallVSTemplates (devenv.exe)](../../ide/reference/installvstemplates-devenv-exe.md) スイッチを使用するには、管理者として devenv を実行する必要があります。 詳細については、[ユーザーのアクセス許可](../../ide/user-permissions-and-visual-studio.md)に関するページを参照してください。

## <a name="syntax"></a>構文

```
devenv.exe /InstallVSTemplates
```

## <a name="see-also"></a>関連項目

[Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)