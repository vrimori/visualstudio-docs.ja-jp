---
title: "インストール後に実行する必要がありますコマンド | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "インストール後のコマンド"
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# インストール後に実行する必要がありますコマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

.Msi ファイルを使用して拡張機能を展開する場合は実行 `devenv/setup` Visual Studio で、拡張機能を検出するために、インストールの一部として。  
  
> [!NOTE]
>  このトピックの情報は、Visual Studio 2008 以前のバージョンと DevEnv の検索に適用されます。 以降のバージョンの Visual Studio を DevEnv を検出する方法については、次を参照してください。 [システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)します。  
  
## Devenv.exe を検索します。  
 各バージョンを見つけることができます値をレジストリから devenv.exe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] RegLocator テーブルと AppSearch テーブルを使用して、プロパティとしてレジストリ値を格納する、インストーラーを記述します。 詳細については、「[システム要件の検出](../../extensibility/internals/detecting-system-requirements.md)」を参照してください。  
  
### RegLocator テーブルの行から別のバージョンの Visual Studio の devenv.exe を検索するには  
  
|Signature\_|ルート|キー|名前|型|  
|-----------------|---------|--------|--------|-------|  
|RL\_DevenvExe\_2002|2|SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2003|2|SOFTWARE\\Microsoft\\VisualStudio\\7.1\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2005|2|SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Setup\\VS|EnvironmentPath|2|  
|RL\_DevenvExe\_2008|2|SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS|EnvironmentPath|2|  
  
### 対応する RegLocator テーブル行のテーブル行の AppSearch  
  
|プロパティ|Signature\_|  
|-----------|-----------------|  
|DEVENV\_EXE\_2002|RL\_DevenvExe\_2002|  
|DEVENV\_EXE\_2003|RL\_DevenvExe\_2003|  
|DEVENV\_EXE\_2005|RL\_DevenvExe\_2005|  
|DEVENV\_EXE\_2008|RL\_DevenvExe\_2008|  
  
 たとえば、Visual Studio インストーラーがのレジストリ値を書き込む **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\Setup\\VS\\EnvironmentPath** として **C:\\VS2008\\Common7\\IDE\\devenv.exe**, 、インストーラーを実行する必要があります実行可能ファイルへの完全パス。  
  
 **注** RegLocator 型の列が 2 であるために、署名の表に、追加のバージョン情報を指定する必要はありません。  
  
## Devenv.exe を実行しています。  
 インストーラーに標準のアクションが実行される AppSearch 後、は、AppSearch テーブル内の各プロパティは、対応するバージョンの Visual Studio の devenv.exe ファイルを指す値を持ちます。 指定されたレジストリ値のいずれかが存在しないかどうか、そのバージョンの Visual Studio がインストールされていないため — 指定したプロパティを設定を null にします。  
  
 カスタムの操作によってプロパティがポイントする実行可能ファイルを実行している Windows インストーラーのサポートは、50 を入力します。 カスタム アクションには、VSPackage に統合する前に正常にインストールされていることを確認するには、スクリプトの実行オプション、msidbCustomActionTypeInScript \(1024\) と msidbCustomActionTypeCommit \(512\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 詳細については、CustomAction テーブルおよびカスタム アクション スクリプトの実行オプションを参照してください。  
  
 50 の種類のカスタム動作では、基になる列と \[ターゲット\] 列のコマンドラインの引数の値として、実行可能ファイルを含むプロパティを指定します。  
  
### Devenv.exe を実行する CustomAction テーブル行  
  
|アクション|型|ソース|ターゲット|  
|-----------|-------|---------|-----------|  
|CA\_RunDevenv2002|1586|DEVENV\_EXE\_2002|\/setup|  
|CA\_RunDevenv2003|1586|DEVENV\_EXE\_2003|\/setup|  
|CA\_RunDevenv2005|1586|DEVENV\_EXE\_2005|\/setup|  
|CA\_RunDevenv2008|1586|DEVENV\_EXE\_2008|\/setup|  
  
 カスタム アクションは、インストール中に実行するためにスケジュールを設定する InstallExecuteSequence テーブルに記述されている必要があります。 カスタム動作をする場合に実行されるを防ぐために、\[条件\] 列の各列に対応するプロパティを使用してバージョンの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] システムにインストールされていません。  
  
> [!NOTE]
>  `Null` プロパティが評価される `False` 条件で使用するとします。  
  
 各カスタム アクションのシーケンス列の値は、Windows インストーラー パッケージには、その他のシーケンス値に依存します。 シーケンスの値は、devenv.exe のカスタム アクションとして実行にできるだけ近い InstallFinalize 標準アクションの直前になるようにする必要があります。  
  
### Devenv.exe のカスタム アクションをスケジュールする InstallExecuteSequence テーブル  
  
|アクション|状態|シーケンス|  
|-----------|--------|-----------|  
|CA\_RunDevenv2002|DEVENV\_EXE\_2002|6602|  
|CA\_RunDevenv2003|DEVENV\_EXE\_2003|6603|  
|CA\_RunDevenv2005|DEVENV\_EXE\_2005|6605|  
|CA\_RunDevenv2008|DEVENV\_EXE\_2008|6608|  
  
## 参照  
 [Windows インストーラーである Vspackage をインストールします。](../../extensibility/internals/installing-vspackages-with-windows-installer.md)