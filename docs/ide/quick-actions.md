---
title: "クイック アクション | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload: multiple
ms.openlocfilehash: 259e033aa32caaca59f37d7dc77ac095b4709878
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="quick-actions"></a>クイック アクション

クイック アクションを使うと、コードのリファクタリング、生成、その他の変更を、1 つの操作で簡単に行うことができます。 クイック アクションは、C#、[C++](/cpp/ide/writing-and-refactoring-code-cpp)および Visual Basic のコード ファイルで使用できます。 クイック アクションには、言語に固有のものと、すべての言語が対象になるものがあります。

クイック アクションは、電球アイコン ![小さい電球アイコン](media/vs2015_lightbulbsmall.png) を使うか、適切なコード行にカーソルを置いて **Ctrl**+ **キーを押すと** 適用できます。 赤い波線が表示され、Visual Studio が問題の修正候補を提供できる場合に、電球アイコンが表示されます。 たとえば、赤い波線で示されるエラーがある場合、そのエラーの修正が可能な場合に電球マークが表示されます。

いずれの言語でも、サードパーティは、たとえば SDK の一部として、カスタマイズした診断や提案を表示できます。Visual Studio はそれらの規則に基づいて電球マークを表示します。

## <a name="to-see-a-light-bulb"></a>電球マークを表示するには

1. 多くの場合、電球マークはマウスをエラーの地点に移動すると自動的に表示されます。あるいは、カレットをエラーのある行に移動すると、エディターの左端に表示されます。 赤い波線が表示されている場合にマウス ポインターを重ねると電球マークを表示させることができます。 問題が発生した行のどこかに、マウスやキーボードを使用して移動することで電球マークを表示させることもできます。

1. 行の任意の場所で **Ctrl**+**.** キーを押すと、 電球マークの表示を呼び出して修正候補のリストを直接表示できます。

   ![電球でのマウス ホバー](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>修正候補を表示するには

下矢印をクリックするか、修正候補を表示するリンクをクリックすると、電球マークで実行可能なクイック操作のリストが表示されます。

![拡大電球](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="see-also"></a>関連項目

[Visual Studio でのコード生成](../ide/code-generation-in-visual-studio.md)  
[共通のクイック アクション](../ide/common-quick-actions.md)  
[コード スタイルとクイック アクション](../ide/code-styles-and-quick-actions.md)  
[コードの作成とリファクタリング (C++)](/cpp/ide/writing-and-refactoring-code-cpp)