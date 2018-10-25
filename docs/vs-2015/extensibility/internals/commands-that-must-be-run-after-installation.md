---
title: インストール後に実行する必要がありますコマンド |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f4db28e933d1f328b71b225ceeeb2b414cd0627b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253800"
---
# <a name="commands-that-must-be-run-after-installation"></a>インストール後に実行する必要があるコマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

実行する必要があります、.msi ファイルから拡張機能をデプロイする場合`devenv /setup`Visual Studio 拡張機能を検出するために、インストールの一部として。  
  
> [!NOTE]
>  このトピックの情報は、Visual Studio 2008 以前のバージョンと DevEnv の検索に適用されます。 以降のバージョンの Visual Studio を DevEnv を検出する方法については、次を参照してください。[システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)します。  
  
## <a name="finding-devenvexe"></a>Devenv.exe の検索  
 各バージョンを見つけることができます値をレジストリから devenv.exe を[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]インストーラーの書き込み、RegLocator テーブルおよび AppSearch テーブルを使用して、レジストリ値をプロパティとして格納します。 詳細については、次を参照してください。[システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)します。  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator テーブルの行から異なるバージョンの Visual Studio の devenv.exe を検索するには  
  
|Signature_|ルート|キー|名前|型|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>AppSearch RegLocator テーブルの行が対応するためのテーブルの行  
  
|プロパティ|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 たとえば、Visual Studio インストーラーがのレジストリ値を書き込む**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath**として**C:\VS2008\Common7\IDE\devenv.exe**、インストーラーを実行する必要があります、実行可能ファイルへの完全パス。  
  
 **注**RegLocator 型の列が 2 であるためには、署名の表に、追加のバージョン情報を指定する必要はありません。  
  
## <a name="running-devenvexe"></a>Devenv.exe を実行しています。  
 インストーラーで標準的なアクションを実行する AppSearch 後、は、AppSearch テーブル内の各プロパティは、対応するバージョンの Visual Studio の devenv.exe ファイルを指す値を持ちます。 指定されたレジストリ値のいずれかが存在しないかどうか、そのバージョンの Visual Studio がインストールされていないため-指定したプロパティを設定を null にします。  
  
 カスタム アクションでプロパティをポイントする実行可能ファイルを実行している Windows インストーラーのサポートは、50 を入力します。 カスタム アクションに統合する前に、VSPackage が正常にインストールされていることを確認するには、スクリプトの実行オプション、msidbCustomActionTypeInScript (1024) および msidbCustomActionTypeCommit (512) を含める必要があります[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 詳細については、CustomAction テーブルとカスタム アクション スクリプトの実行オプションを参照してください。  
  
 50 種類のカスタム アクションは、ソース列と対象の列でコマンドライン引数の値として、実行可能ファイルを含むプロパティを指定します。  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction テーブル行の devenv.exe を実行するには  
  
|アクション|型|ソース|ターゲット|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/setup|  
  
 インストール中に実行をスケジュールして InstallExecuteSequence テーブルには、カスタム アクションを作成する必要があります。 カスタム動作をする場合に実行されるを防ぐために条件列の各列に対応するプロパティを使用してバージョンの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]システムがインストールされていません。  
  
> [!NOTE]
>  `Null` プロパティを評価する`False`条件で使用するとします。  
  
 各カスタム アクションのシーケンス列の値は、Windows インストーラー パッケージには、その他のシーケンス値によって異なります。 シーケンス値は、devenv.exe のカスタム アクションとして実行できるだけ近くに InstallFinalize の標準的な操作の前にすぐになるようになります。  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Devenv.exe のカスタム アクションをスケジュールする InstallExecuteSequence テーブル  
  
|アクション|条件|シーケンス|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラーによる VSPackage のインストール](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

