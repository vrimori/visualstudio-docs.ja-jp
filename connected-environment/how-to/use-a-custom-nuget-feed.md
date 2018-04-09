---
title: Connected Environment でカスタム NuGet フィードを使用する方法| Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 03/27/2018
ms.topic: article
description: カスタム NuGet フィードを使用し、Connected Environment で NuGet パッケージにアクセスし、使用します。
keywords: Docker、Kubernetes、Azure、AKS、Azure Container Service、コンテナー
manager: ghogen
ms.openlocfilehash: 94956e061302281ef232205081346c0aa90eab90
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
#  <a name="use-a-custom-nuget-feed-in-a-connected-environment"></a>接続されている環境でカスタム NuGet フィードを使用する

NuGet フィードは、プロジェクトにパッケージ ソースを含める便利な手段です。 Connected Environment は、Docker コンテナーに依存関係を正しくインストールするために、このフィードにアクセスできる必要があります。

NuGet フィードを設定するには:
1. `PackageReference` ノードの下で `*.csproj` ファイルに[パッケージ参照](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files)を追加します。

   ```xml
   <ItemGroup>
       <!-- ... -->
       <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0" />
       <!-- ... -->
   </ItemGroup>
   ```

2. プロジェクト フォルダーで [NuGet.Config](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file) ファイルを作成します。
     * `packageSources` セクションを使用し、NuGet フィードの場所を参照します。 重要: NuGet フィードにはパブリック アクセスできる必要があります。
     * `packageSourceCredentials` セクションを使用し、ユーザー名とパスワードの資格情報を構成します。 

   ```xml
   <packageSources>
       <add key="Contoso" value="https://contoso.com/packages/" />
   </packageSources>

   <packageSourceCredentials>
       <Contoso>
           <add key="Username" value="user@contoso.com" />
           <add key="ClearTextPassword" value="33f!!lloppa" />
       </Contoso>
   </packageSourceCredentials>
   ```

3. ソース コード管理を利用している場合:
    - ソース リポジトリに誤って資格情報をコミットしないように、`.gitignore` ファイルの `NuGet.Config` を参照します。
    - プロジェクトで `vsce.yaml` ファイルを開き、`build` セクションを見つけます。`NuGet.Config` ファイルが Azure と同期し、コンテナー イメージ構築プロセスで使用されるように次のスニペットを挿入します。 (既定では、Connected Environment は `.gitignore` ルールと `.dockerignore` ルールに一致するファイルを同期しません。)

        ```yaml
        build:
        useGitIgnore: true
        ignore:
        - “!NuGet.Config”
        ```


## <a name="next-steps"></a>次の手順

上記の手順を完了すると、次に `vsce up` を実行したとき (あるいは VSCode か Visual Studio で `F5` を押したとき)、Connected Environment は `NuGet.Config` ファイルを Azure と同期します。`dotnet restore` は Azure を利用し、コンテナーにパッケージ依存関係をインストールします。

