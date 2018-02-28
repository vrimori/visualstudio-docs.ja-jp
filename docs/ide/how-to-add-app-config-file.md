---
title: "Visual Studio でプロジェクトに app.config ファイルを追加する方法 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: d77e86599670ef04b813381da84a03ab1f238af3
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>方法: C# プロジェクトにアプリケーション構成ファイルを追加する

アプリケーション構成ファイル (app.config ファイル) を C# プロジェクトに追加すると、共通言語ランタイムがアセンブリ ファイルを検索し読み込む方法をカスタマイズできます。 アプリケーション構成ファイルの詳細については、「[ランタイムがアセンブリを検索する方法 (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)」を参照してください。

> [!NOTE]
> UWP アプリには、app.config ファイルは含まれていません。

プロジェクトをビルドすると、開発環境が app.config ファイルを自動的にコピーして、実行可能ファイルに一致するようにコピーのファイル名を変更し、そのコピーを **bin** ディレクトリに移動します。

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>C# プロジェクトにアプリケーション構成ファイルを追加するには

1. メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。

     **[新しい項目の追加]** ダイアログ ボックスが表示されます。

1. **[インストール]** > **[Visual C# アイテム]** の順に展開し、**[アプリケーション構成ファイル]** テンプレートを選択します。

3.**[名前]** ボックスに名前を入力し、**[追加]** ボタンをクリックします。

     A file named app.config is added to your project.

## <a name="see-also"></a>関連項目

[アプリケーションの設定の管理 (.NET)](../ide/managing-application-settings-dotnet.md)  
[構成ファイル スキーマ (.NET Framework )](/dotnet/framework/configure-apps/file-schema/index)  
[アプリの構成 (.NET Framework)](/dotnet/framework/configure-apps/index)