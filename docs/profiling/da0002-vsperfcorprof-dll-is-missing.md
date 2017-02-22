---
title: "DA0002: VSPerfCorProf.dll がありません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0002"
  - "vs.performance.2"
  - "vs.performance.rules.DAVsPerfCorProfMissing"
  - "vs.performance.rules.DA0002"
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0002: VSPerfCorProf.dll がありません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|規則 ID|DA0002|  
|分類|プロファイリング ツールの使用|  
|プロファイル方法|VSPerfCmd および VSPerfASPNETCmd のコマンド ライン ツールを使用したプロファイリング|  
|メッセージ|VSPerfCLREnv.cmd で環境変数を正しく設定していない状態でファイルが収集された可能性があります。  マネージ バイナリのシンボルを解決できません。|  
|規則の種類|情報|  
  
## 原因  
 プロファイリング実行中に VSPerfCorProf.dll が見つかりませんでした。  この警告は、VSPerfCLREnv.cmd ツールを使用せずにプロファイラー データ収集用のコマンド ライン ツールを使用して、必要な環境変数を初期化すると発生します。  また、プロファイリング ツールが起動されたときに別のプロファイラーが実行中の場合も、この警告が発生することがあります。  
  
## 規則の説明  
 プロファイラーでプロファイリングを実行して .NET Framework バイナリのシンボルを解決するには、事前に特定の環境変数を設定する必要があります。  この警告は、プロファイル データを収集する前に VSPerfCLREnv.cmd ツールが実行されていなかったことを示します。  マネージ バイナリのシンボルを解決できない場合があります。  コマンド ラインからプロファイリング ツールを使用する方法の詳細については、「[コマンド ラインからのプロファイリング](../profiling/using-the-profiling-tools-from-the-command-line.md)」を参照してください。  
  
## 違反の修正方法  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールのコマンド ライン ツールを使用してマネージ アプリケーションをプロファイリングする場合は、データの収集を開始する前に [VSPerfCLREnv](../profiling/vsperfclrenv.md) コマンド ライン ツールを実行してください。