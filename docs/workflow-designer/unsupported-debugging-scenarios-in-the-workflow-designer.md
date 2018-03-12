---
title: "デバッグする場合、ワークフロー デザイナーでサポートされていない |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 958937e8d846c07cafc8293b4592ad6c67479849
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>ワークフロー デザイナーでサポートされていないデバッグ シナリオ
[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] のワークフロー デザイナーには多くの新機能が追加されていますが、いくつかサポートされていないデバッグ シナリオがあります。 このドキュメントでは、サポートされていないワークフロー デザイナーのデバッグ シナリオについて詳しく説明します。  
  
-   コードを編集した後では実行を続行できません。  
  
-   ワークフローの任意の場所から実行を続行することはできません (次の設定)。  
  
-   カーソルが到達するまで実行を続行できません (カーソル行の前まで実行)。  
  
-   デザイナーを使用せずにコード内に作成されたワークフローをデバッグするためにワークフロー デザイナーを使用することはできません。  
  
-   以前のバージョンの [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] で作成されたワークフローを [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] デザイナーでデバッグすることはできません。  
  
-   アクティビティまたは <xref:System.Activities.Statements.Flowchart> ノード間のリンクにブレークポイントを定義することはできません。  
  
-   クリップボードは、デバッグ時には使用できません。  
  
-   アクティビティをコピーまたは貼り付けた場合にはブレークポイントは保持されません。  
  
-   ワークフローのブレークポイントを呼び出し履歴ウィンドウに設定することはできません。  
  
-   デザイナーでブレークポイントを作成するときに、**行**と**文字**の設定、**新しいブレークポイント** ダイアログ ボックスは使用されません。  
  
-   [ブレークポイント] ウィンドウまたはショートカット メニューは、ワークフローのデバッグで、次の列またはオプションをサポートしていません。  
  
    -   状態  
  
    -   ヒット カウント  
  
    -   ヒット時   
  
    -   関数  
  
    -   データ  
  
    -   プロセス  
  
    -   逆アセンブルを表示