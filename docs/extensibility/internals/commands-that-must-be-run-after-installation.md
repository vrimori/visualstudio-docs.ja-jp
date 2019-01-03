---
title: インストール後に実行する必要がありますコマンド |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 691cabb67df53faf23c23e2fa3f05f0ca68038a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915550"
---
# <a name="commands-that-must-be-run-after-installation"></a>インストール後に実行する必要がありますコマンド
使用して、拡張機能をデプロイする場合、 *.msi*ファイルが実行する必要があります**devenv/setup** Visual Studio 拡張機能を検出するために、インストールの一部として。  
  
> [!NOTE]
>  このトピックの情報が検索に適用されます*devenv.exe* Visual Studio 2008 以前のバージョンとします。 検出する方法については*devenv.exe*以降のバージョンの Visual Studio では、次を参照してください。[システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)します。  
  
## <a name="find-devenvexe"></a>Devenv.exe を検索します。  
 各バージョンを見つけることができます*devenv.exe*値をレジストリから[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]インストーラーの書き込み、RegLocator テーブルおよび AppSearch テーブルを使用して、レジストリ値をプロパティとして格納します。 詳細については、次を参照してください。[システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)します。  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator テーブルの行から異なるバージョンの Visual Studio の devenv.exe を検索するには  
  
|署名|ルート|キー|名前|型|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch RegLocator テーブルの行が対応するためのテーブルの行  
  
|プロパティ|署名|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 たとえば、Visual Studio インストーラーがのレジストリ値を書き込む**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath**として*C:\VS2008\Common7\IDE\devenv.exe*、インストーラーを実行する必要があります、実行可能ファイルへの完全パス。  
  
> [!NOTE]
> RegLocator テーブルの型の列が 2 であるために、署名の表に追加のバージョン情報を指定する必要はありません。  
  
## <a name="run-devenvexe"></a>Devenv.exe を実行します。  
 AppSearch テーブル内の各プロパティが指す値を持つインストーラーの標準的なアクションを実行する AppSearch、後に、 *devenv.exe*対応するバージョンの Visual Studio 用のファイル。 指定されたレジストリ値のいずれかが存在しないかどうか、そのバージョンの Visual Studio がインストールされていないため-指定したプロパティを設定を null にします。  
  
 カスタム アクションでプロパティをポイントする実行可能ファイルを実行している Windows インストーラーのサポートは、50 を入力します。 カスタム アクションは、スクリプトの実行オプションを含める必要があります`msidbCustomActionTypeInScript`(1024) と`msidbCustomActionTypeCommit`に統合する前に、VSPackage が正常にインストールされていることを確認する (512)、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 詳細については、次を参照してください。 [CustomAction テーブル](https://docs.microsoft.com/windows/desktop/msi/customaction-table)と[カスタム アクション スクリプトの実行オプション](https://docs.microsoft.com/windows/desktop/msi/custom-action-in-script-execution-options)します。  
  
 50 種類のカスタム アクションは、ソース列と対象の列でコマンドライン引数の値として、実行可能ファイルを含むプロパティを指定します。  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction テーブル行の devenv.exe を実行するには  
  
|アクション|型|ソース|ターゲット|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|  
  
 インストール中に実行をスケジュールして InstallExecuteSequence テーブルには、カスタム アクションを作成する必要があります。 カスタム動作をする場合に実行されるを防ぐために条件列の各列に対応するプロパティを使用してバージョンの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]システムがインストールされていません。  
  
> [!NOTE]
>  Null 値のプロパティが評価される`False`条件で使用するとします。  
  
 各カスタム アクションのシーケンス列の値は、Windows インストーラー パッケージには、その他のシーケンス値によって異なります。 シーケンス値にする必要がありますように、 *devenv.exe*として実行するカスタム アクションにできるだけ近い InstallFinalize の標準的な操作の前にすぐにします。  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Devenv.exe のカスタム アクションをスケジュールする InstallExecuteSequence テーブル  
  
|アクション|条件|シーケンス|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラーによる Vspackage をインストールします。](../../extensibility/internals/installing-vspackages-with-windows-installer.md)