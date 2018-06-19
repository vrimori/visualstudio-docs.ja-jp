---
title: ワークフロー デザイナーの従来のステート マシン ワークフロー デザイナーの使用
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6ad09c2e999d9432b3c4e1062cb3031eb20ff56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979150"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>従来のステート マシン ワークフロー デザイナーの使用

新しいステート マシン ワークフロー プロジェクトを作成する、.NET Framework version 3.5、または、WinFX を対象とする Visual Studio 2010 では、ときに、いずれかを使用することもできます、**ステート マシン ワークフロー コンソール アプリケーション**または、 **ステート マシン ワークフロー ライブラリ**レガシ プロジェクト テンプレート。 これらのいずれかのステート マシン プロジェクト テンプレートを選択した場合、ステート マシン デザイナーが従来のワークフロー デザイナーのユーザー インターフェイスとして表示されます。 従来のステート マシン プロジェクト テンプレートの概要については、次を参照してください[する方法: 作成状態マシン ワークフロー コンソール アプリケーション (レガシ)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)と[する方法: ステート マシン ワークフロー ライブラリ (レガシ)作成](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

ステート マシン ワークフローは、ステート (状態) のセットで構成されます。 1 つのステートが初期状態として設定されます。 各ステートは特定のイベント セットを受信できます。 イベントに基づいて、別のステートへの移行を実行できます。 ステート マシン ワークフローには最終ステートを定義できます。 最終ステートに移行すると、ワークフローは完了します。

## <a name="state-machine-designer-views"></a>ステート マシン デザイナーのビュー
 ステート マシン デザイナーは自由度の高いデザイナーです。デザイン サーフェイス上でアクティビティを自由に移動することができます。 ステート マシン デザイナーが 2 つのビュー:*状態*ビューと*イベント ドリブン*ビュー。

 ステート ビューには、ステート アクティビティ、およびステート アクティビティ内に格納されているイベントドリブン アクティビティが表示されます。 このビューでは、1 つのステートから別のステートへの移行が、1 つのステート内のイベントドリブン アクティビティから別のステートに伸びる線として表されます。 また、独自の線を描くことにより、移行を作成することもできます。 移行を描くには、イベントドリブン アクティビティを選択し、アクティビティ上のいずれかのハンドルを選択して、それをドラッグします。 この操作によって、線が描画されます。 次に、この線が移行先のステートに接続されて、2 つのステート間の移行を表します。

 イベントドリブン ビューにアクセスするには、いずれかのイベントドリブン アクティビティをダブルクリックします。 シーケンシャル ワークフロー デザイナーに似たデザイナーが表示されます。 デザイナー上部のナビゲーション バーには、表示されるイベントドリブン アクティビティまでのアクティビティ階層が示されます。 表示されている階層内のいずれかの要素をクリックすると、元のステート ビューに移動できます。 ステート ビューで 1 つのステートから別のステートへの移行を描画した後、そのアクティビティのイベントドリブン ビューを表示する場合は、設定済みのステート アクティビティがイベントドリブン アクティビティに自動的に追加されます。 設定済みのステート アクティビティのプロパティを変更すると、その変更が元のステート ビューに反映されます。

## <a name="state-machine-workflow-activities"></a>ステート マシン ワークフローのアクティビティ
 ステート マシン ワークフロー デザイナーで使用される主なアクティビティを次の表で説明します。

|ツールボックス名|アクティビティ|説明|
|------------------|--------------|-----------------|
|**状態**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|ステート マシン; の状態を表しますその他を含めることがあります**StateActivity**アクティビティ。 詳細については、次を参照してください。 [StateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65083)です。|
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|新しいステート (状態) への移行を指定します。 詳細については、次を参照してください。 [SetStateActivity アクティビティを使用して](http://go.microsoft.com/fwlink?LinkID=65082)です。|
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|あるステートに移行する (他のアクティビティも同時に指定可) と実行されます。 詳細については、次を参照してください。 [StateInitialization アクティビティ](http://go.microsoft.com/fwlink?LinkID=65006)です。|
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|終了するときに含まれているアクティビティを実行、 [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)アクティビティ。 詳細については、次を参照してください。 [StateFinalizationActivity アクティビティ](http://go.microsoft.com/fwlink?LinkID=65008)です。|
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|外部イベントによって実行開始されるステートに使用されます。 **EventDrivenActivity**アクティビティにアクティビティを実装する必要があります、 [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032)最初の子アクティビティとしてインターフェイスです。 詳細については、次を参照してください。 [EventDrivenActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65068)です。|

 ステート マシン ワークフローの主なコンポーネントは、 [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)アクティビティ。 ステート マシン ワークフロー内のさまざまなポイントでイベントがキャプチャされると、イベントに関連したタスクを処理するさまざまなステートに移行します。 有効期間中、ワークフローはいくつかの異なるステート間を遷移します。 使用して、これらの状態が相互に接続、 [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)アクティビティ。

 新しいをドラッグすると**StateActivity**ワークフロー デザイン サーフェイスに追加することができます[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)、 [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)、 [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)、または追加**StateActivity**アクティビティが子アクティビティとして。

> [!CAUTION]
> ステート マシン ワークフロー デザイナーを使用してワークフローを作成する場合を使用したデザインは、ワークフローの構造を監視する必要があります、 **[ドキュメント アウトライン**ビュー] ウィンドウ。 ステート マシン ワークフローの構造のビュー、 **ドキュメント アウトライン**ビュー ウィンドウがワークフロー マークアップ ファイル内のアクティビティの論理的レイアウトを表します。 デザイン サーフェイスに表示されるワークフロー アクティビティの物理的レイアウトは、ワークフロー マークアップ ファイル内のアクティビティの論理的レイアウトを表さない可能性があります。
>
> 開くには、 **ドキュメント アウトライン** ウィンドウで、**ビュー**  メニューのをポイント**その他のウィンドウ**、し、 **ドキュメント アウトライン**です。

## <a name="see-also"></a>関連項目

- [方法: ステート マシン ワークフロー コンソール アプリケーションを作成する (レガシ)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)
- [方法: ステート マシン ワークフロー ライブラリを作成する (レガシ)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)
- [ステート マシン ワークフロー](http://go.microsoft.com/fwlink?LinkID=65016)
- [StateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65083)
- [StateInitializationActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65006)
- [StateFinalizationActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65008)
- [SetStateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65082)
- [EventDrivenActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65068)