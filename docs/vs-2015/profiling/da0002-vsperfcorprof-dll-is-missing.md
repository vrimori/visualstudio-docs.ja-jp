---
title: 'DA0002: VSPerfCorProf.dll がありません | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb1359b525b286dbc88cbd3d8eecaef27060ab23
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809468"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll がありません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA 0002 |  
|カテゴリ |プロファイリング ツールの使用 |  
|プロファイル方法 |VSPerfCmd と VSPerfASPNETCmd コマンド ライン ツールを使用したプロファイリング |  
|メッセージ |VSPerfCLREnv.cmd で環境変数を正しく設定しないままファイルが収集されたことが表示されます。 マネージ バイナリのシンボルが解決されない場合があります |。  
|規則の種類 |情報 |  
  
## <a name="cause"></a>原因  
 プロファイラーは、プロファイリング実行中、VSPerfCorProf.dll を見つけることができませんでした。 プロファイラー データを集めるためのコマンドライン ツールが VSPerfCLREnv.cmd ツールで必要な環境変数を初期化することなく使用されたとき、この警告が発生します。 プロファイリング ツールの開始時に別のプロファイラーが実行されていた場合にもこの警告は発生します。  
  
## <a name="rule-description"></a>規則の説明  
 プロファイラーのプロファイリング実行で .NET Framework バイナリのシンボルを解決するには、特定の環境変数を設定する必要があります。 この警告が示唆することは、プロファイリング データが集められる前に VSPerfCLREnv.cmd ツールが実行されなかったということです。 マネージド バイナリのシンボルを解決できないことがあります。 コマンドラインからプロファイリング ツールを使用する方法については、[コマンド ラインからのプロファイリング](../profiling/using-the-profiling-tools-from-the-command-line.md)に関するページを参照してください。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロファイリング ツールのコマンドライン ツールを利用してマネージド アプリケーションをプロファイリングするとき、データの収集を開始する前に [VSPerfCLREnv](../profiling/vsperfclrenv.md) コマンドライン ツールを実行します。



