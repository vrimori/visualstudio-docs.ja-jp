---
title: "プロファイリング ツールの使用に関する規則 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# プロファイリング ツールの使用に関する規則
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロファイル ツールの使用カテゴリのパフォーマンス規則は、データを最も効率よく収集するためのプロファイラーの使用に関するガイドラインを提供します。  
  
|||  
|-|-|  
|[DA0002: VSPerfCorProf.dll がありません](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|コマンド ライン プロファイルに、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] バイナリの不完全なデータが含まれている可能性があります。  これは、正しい環境変数が設定されていないことが原因である場合があります。|  
|[DA0003: カーネル サンプルが多数存在します](../profiling/da0003-many-kernel-samples.md)|対象バイナリの実行以外で生成された多くのプロファイル サンプルが記録されています。  より正確なデータを収集するには、インストルメンテーション メソッドの使用を検討してください。|  
|[DA0004: プロセッサ使用率が高くなっています](../profiling/da0004-high-processor-usage.md)|プロファイル データは、プロファイリング実行中にプロセッサが常にビジー状態であったことを示しています。  より正確なデータを収集するには、サンプリング メソッドの使用を検討してください。|  
|[DA0008: 少数のサンプルしか収集されていません](../profiling/da0008-few-samples-collected.md)|プロファイリング実行で収集されたサンプルの数が、統計的に有意な数には足りませんでした。  もう一度プロファイリングを実行し、これまでよりも長い時間アプリケーションを実行してください。  また、インストルメンテーション メソッドを使用してデータを収集することも検討してください。|  
|[DA0026: 過剰なカーネル CPU 処理時間。](../Topic/DA0026:%20Excessive%20kernel%20CPU%20time%20processing.md)|プロセッサのカーネル モードではプロファイリング実行に非常に時間がかかりました。  サンプリングで、時間をメトリックとして使用するのではなく、システム コールをメトリックとして使用することを検討してください。|  
|[DA0029: サポートされていない CLR バージョンです。](../profiling/da0029-unsupported-clr-version.md)|プロファイルされるバイナリが、プロファイラーでサポートされない [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] バージョンを使用しています。  プロファイラー レポートはシンボル名を解決できません。|  
|[DA0030: データベース プロジェクトの階層の相互作用の測定を収集します。](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|<xref:System.Data?displayProperty=fullName> 名前空間で多数のメソッドの呼び出しが収集されました。  データベース コールに関するデータを含めるには、プロファイル実行で階層相互作用データの収集を検討してください。|