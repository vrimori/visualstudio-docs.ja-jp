---
title: Azure のコマンド ライン ビルド |Microsoft Docs
description: Azure のコマンド ライン ビルド
author: ghogen
manager: douge
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: fce752d91ebaa765e18efef117a3b6efe750119c
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002939"
---
# <a name="building-azure-projects-from-the-command-line"></a>コマンドラインからの Azure プロジェクトのビルド
Microsoft Build Engine (MSBuild) を使用して、Visual Studio がインストールされていないビルド ラボ環境で製品を構築できます。 MSBuild の拡張可能な Microsoft によって完全にサポートされているプロジェクト ファイルの XML 形式を使用します。 MSBuild ファイル形式を使用して記述できます項目のために必要な 1 つまたは複数のプラットフォームや構成用にビルドされました。

、コマンドラインで MSBuild を実行することもでき、このトピックでは、その方法を説明します。 コマンドラインでプロパティを設定して、プロジェクトの特定の構成を構築できます。 同様に、MSBuild でビルドするターゲットを定義することもできます。 コマンド ライン パラメーターおよび MSBuild の詳細については、次を参照してください。 [MSBuild コマンド ライン リファレンス](https://msdn.microsoft.com/library/ms164311.aspx)します。

## <a name="msbuild-parameters"></a>MSBuild パラメーター
パッケージを作成する最も簡単な方法が MSBuild を実行するには、`/t:Publish`オプション。 既定では、このディレクトリが作成されます、プロジェクトのルート フォルダーなど`<ProjectDirectory>\bin\Configuration\app.publish\`します。 Azure プロジェクトをビルドすると 2 つのファイルが生成されます。 パッケージ ファイル自体と付随する構成ファイル。

* パッケージ ファイル (`project.cspkg`)
* 構成ファイル (`ServiceConfiguration.TargetProfile.cscfg`)

既定では、各 Azure プロジェクトには、ローカル (デバッグ) ビルド用の 1 つのサービス構成ファイルとクラウド (ステージングまたは運用) ビルドが含まれています。 ただし、追加したり、必要に応じてサービス構成ファイルを削除できます。 Visual Studio 内でパッケージをビルドするときに、パッケージに含めるサービス構成ファイルを指定を求められます。 MSBuild を使用してパッケージをビルドするときに、既定では、ローカル サービス構成ファイルが含まれています。 別のサービス構成ファイルを含めるには設定、 `TargetProfile` MSBuild コマンドのプロパティ (`MSBuild /t:Publish /p:TargetProfile=ProfileName`)。

格納されたパッケージと構成ファイルの別のディレクトリを使用する場合は、パスを設定を使用して、`/p:PublishDir=Directory\`オプションで、末尾にバック スラッシュ区切り記号。

## <a name="next-steps"></a>次の手順
パッケージをビルドすると後、は、Azure にデプロイすることができます。