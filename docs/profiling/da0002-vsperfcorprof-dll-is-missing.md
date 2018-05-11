---
title: 'DA0002: VSPerfCorProf.dll がありません | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd86c14b9364bc9dfe7796cfdedc80f270fa52bf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll がありません
|||  
|-|-|  
|規則 ID|DA0002|  
|カテゴリ|プロファイリング ツールの使用|  
|プロファイル方法|コマンド ライン ツールの VSPerfCmd と VSPerfASPNETCmd を使用してプロファイリングする|  
|メッセージ|VSPerfCLREnv.cmd で環境変数を正しく設定しないままファイルが収集されたようです。 マネージ バイナリのシンボルを解決できません。|  
|規則の種類|情報|  
  
## <a name="cause"></a>原因  
 プロファイラーは、プロファイリング実行中、VSPerfCorProf.dll を見つけることができませんでした。 プロファイラー データを集めるためのコマンドライン ツールが VSPerfCLREnv.cmd ツールで必要な環境変数を初期化することなく使用されたとき、この警告が発生します。 プロファイリング ツールの開始時に別のプロファイラーが実行されていた場合にもこの警告は発生します。  
  
## <a name="rule-description"></a>規則の説明  
 プロファイラーのプロファイリング実行で .NET Framework バイナリのシンボルを解決するには、特定の環境変数を設定する必要があります。 この警告が示唆することは、プロファイリング データが集められる前に VSPerfCLREnv.cmd ツールが実行されなかったということです。 マネージ バイナリのシンボルを解決できないことがあります。 コマンドラインからプロファイリング ツールを使用する方法については、[コマンド ラインからのプロファイリング](../profiling/using-the-profiling-tools-from-the-command-line.md)に関するページを参照してください。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールのコマンドライン ツールを利用してマネージ アプリケーションをプロファイリングするとき、データの収集を開始する前に [VSPerfCLREnv](../profiling/vsperfclrenv.md) コマンドライン ツールを実行します。