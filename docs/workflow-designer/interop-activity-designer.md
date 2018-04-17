---
title: Interop アクティビティ デザイナー |Microsoft ドキュメント
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbac122e2e12844249be8dad37d6bed65b90ddc3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="interop-activity-designer"></a>Interop アクティビティ デザイナー
**相互運用機能**アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.Interop>アクティビティ。

## <a name="the-interop-activity"></a>Interop アクティビティ
 <xref:System.Activities.Statements.Interop> アクティビティでは、ワークフロー内の <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> から派生する型の実行を管理します。

### <a name="using-the-interop-activity-designer"></a>Interop アクティビティ デザイナーの使用
 **相互運用機能**アクティビティ デザイナーは含まれて、**移行**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス** タブ (または、選択**ツールボックス**から、**ビュー**メニューまたは CTRL + ALT + X です)。

 [移行](../workflow-designer/migration-activity-designers.md)含まれているカテゴリ、<xref:System.Activities.Statements.Interop>アクティビティのみに表示、**ツールボックス**場合は、プロジェクトのすべてのターゲット[!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)]です。

 C# プロジェクトの場合、完全を使用するプロジェクトをターゲットするを再[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]でプロジェクトを右クリックして、**ソリューション エクスプ ローラー**を選択して**プロパティ**です。 **アプリケーション**] タブで、[、 **NET Framework 4**オプション、**ターゲット フレームワーク**です。 選択、 **[はい]**ボタンをクリックして、**ターゲット フレームワークの変更**ダイアログがこの変更の確認を求めるを表示します。

 VB プロジェクトの場合、完全を使用するプロジェクトをターゲットするを再[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)]でプロジェクトを右クリックして、**ソリューション エクスプ ローラー**を選択して**プロパティ**です。 **コンパイル**タブをクリックし、**詳細コンパイル オプション**ボタンをクリックします。 選択**.Net Framework 4**から、**対象のフレームワーク リスト** をクリックし、 **ok**です。 クリックして、**はい**ボタンをクリックして、**ターゲット フレームワークの変更**すると、この変更の確認を求めるために表示されるダイアログ。

 **相互運用機能**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>です。 これを作成、 <xref:System.Activities.Statements.Interop> 、既定値を持つアクティビティ**DisplayName**の相互運用機能します。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、**相互運用機能**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

 クリックして、 **[参照] をクリックしています.**内のテキスト、 **ActivityType**ボックスで、いずれかで、**相互運用機能**アクティビティ デザイナーまたはプロパティ グリッドを呼び出すことで、**型の参照と選択 .Net**ダイアログ ボックス。 ワークフロー 3.0 またはワークフロー 3.5 のアクティビティの型のみ (つまり、<xref:System.Workflow.ComponentModel.Activity> から派生した型のみ) が表示されます。 このボックスを使用して、型を指定する方法の詳細については、次を参照してください。、[参照し、.NET の種類 ダイアログ ボックスをオンに](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)トピックです。

### <a name="the-interop-properties"></a>Interop のプロパティ
 次の表に、<xref:System.Activities.Statements.Interop> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドまたは[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できます。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> アクティビティの表示名。 既定値は Interop です。 表示名は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|<xref:System.Activities.Statements.Interop> アクティビティに含まれているアクティビティの型を指定します。 指定されたこの型は、<xref:System.Workflow.ComponentModel.Activity> から派生していることが必要です。|

## <a name="see-also"></a>関連項目

- [移行](../workflow-designer/migration-activity-designers.md)