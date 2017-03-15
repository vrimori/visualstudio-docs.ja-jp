---
title: "従来のステート マシン ワークフロー デザイナーの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "EventDrivenActivity アクティビティ"
  - "SetStateActivity アクティビティ"
  - "ステート マシン ワークフロー デザイナー"
  - "ステート マシン ワークフロー, アクティビティ"
  - "ステート マシン ワークフロー, デザイナー"
  - "StateActivity アクティビティ"
  - "StateFinalizationActivity アクティビティ"
  - "StateInitializationActivity アクティビティ"
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 従来のステート マシン ワークフロー デザイナーの使用
[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] で新しいステート マシン ワークフロー プロジェクトを作成するとき、従来の **\[ステート マシンのワークフロー コンソール アプリケーション\]** または **\[ステート マシンのワークフロー ライブラリ\]** プロジェクト テンプレートを使用するように選択できます。これらのいずれかのステート マシン プロジェクト テンプレートを選択した場合、ステート マシン デザイナーが従来のワークフロー デザイナーのユーザー インターフェイスとして表示されます。従来のステート マシン プロジェクト テンプレートの詳細については、「[方法: ステート マシン ワークフロー コンソール アプリケーションを作成する \(レガシ\)](../Topic/How%20to:%20Create%20State%20Machine%20Workflow%20Console%20Applications%20\(Legacy\).md)」および「[方法: ステート マシン ワークフロー ライブラリを作成する \(レガシ\)](../Topic/How%20to:%20Create%20a%20State%20Machine%20Workflow%20Library%20\(Legacy\).md)」を参照してください。  
  
 ステート マシン ワークフローは、ステート \(状態\) のセットで構成されます。1 つのステートが初期状態として設定されます。各ステートは特定のイベント セットを受信できます。イベントに基づいて、別のステートへの移行を実行できます。ステート マシン ワークフローには最終ステートを定義できます。最終ステートに移行すると、ワークフローは完了します。  
  
## ステート マシン デザイナーのビュー  
 ステート マシン デザイナーは自由度の高いデザイナーです。デザイン サーフェイス上でアクティビティを自由に移動することができます。ステート マシン デザイナーには、*ステート* ビューと*イベントドリブン* ビューの 2 つのビューがあります。  
  
 ステート ビューには、ステート アクティビティ、およびステート アクティビティ内に格納されているイベントドリブン アクティビティが表示されます。このビューでは、1 つのステートから別のステートへの移行が、1 つのステート内のイベントドリブン アクティビティから別のステートに伸びる線として表されます。また、独自の線を描くことにより、移行を作成することもできます。移行を描くには、イベントドリブン アクティビティを選択し、アクティビティ上のいずれかのハンドルを選択して、それをドラッグします。この操作によって、線が描画されます。次に、この線が移行先のステートに接続されて、2 つのステート間の移行を表します。  
  
 イベントドリブン ビューにアクセスするには、いずれかのイベントドリブン アクティビティをダブルクリックします。シーケンシャル ワークフロー デザイナーに似たデザイナーが表示されます。デザイナー上部のナビゲーション バーには、表示されるイベントドリブン アクティビティまでのアクティビティ階層が示されます。表示されている階層内のいずれかの要素をクリックすると、元のステート ビューに移動できます。ステート ビューで 1 つのステートから別のステートへの移行を描画した後、そのアクティビティのイベントドリブン ビューを表示する場合は、設定済みのステート アクティビティがイベントドリブン アクティビティに自動的に追加されます。設定済みのステート アクティビティのプロパティを変更すると、その変更が元のステート ビューに反映されます。  
  
## ステート マシン ワークフローのアクティビティ  
 ステート マシン ワークフロー デザイナーで使用される主なアクティビティを次の表で説明します。  
  
|ツールボックス名|アクティビティ|説明|  
|--------------|-------------|--------|  
|**State**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|ステート マシン内のステート \(状態\) を表します。追加の **StateActivity** アクティビティが含まれる場合があります。詳細については、「[StateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65083)」を参照してください。|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|新しいステートへの移行を指定します。詳細については、「[SetStateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65082)」を参照してください。|  
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|あるステートに移行する \(他のアクティビティも同時に指定可\) と実行されます。詳細については、「[StateInitialization アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65006)」を参照してください。|  
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) アクティビティを終了するときに、格納されているアクティビティを実行します。詳細については、「[StateFinalizationActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65008)」を参照してください。|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|外部イベントによって実行開始されるステートに使用されます。**EventDrivenActivity** アクティビティは、[IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) インターフェイスを実装するアクティビティを、最初の子アクティビティとして持つ必要があります。詳細については、「[EventDrivenActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65068)」を参照してください。|  
  
 ステート マシン ワークフローの主なコンポーネントは、[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) アクティビティです。ステート マシン ワークフロー内のさまざまなポイントでイベントがキャプチャされると、イベントに関連したタスクを処理するさまざまなステートに移行します。有効期間中、ワークフローはいくつかの異なるステート間を遷移します。これらのステートは、[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) アクティビティを使って相互に接続されます。  
  
 新しい **StateActivity** をワークフロー デザイン サーフェイス上にドラッグするとき、[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)、[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)、[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)、または追加の **StateActivity** アクティビティを子アクティビティとして追加できます。  
  
> [!CAUTION]
>  ステート マシン ワークフロー デザイナーを使ってワークフローを作成するとき、設計中のワークフローの構造を **\[ドキュメント アウトライン\]** ビュー ウィンドウで監視する必要があります。**\[ドキュメント アウトライン\]** ビュー ウィンドウに表示されるステート マシン ワークフローの構造は、ワークフロー マークアップ ファイル内のアクティビティの論理的レイアウトを表します。デザイン サーフェイスに表示されるワークフロー アクティビティの物理的レイアウトは、ワークフロー マークアップ ファイル内のアクティビティの論理的レイアウトを表さない可能性があります。  
>   
>  **\[ドキュメント アウトライン\]** ウィンドウを表示するには、**\[表示\]** メニューの **\[その他のウィンドウ\]** をポイントして、**\[ドキュメント アウトライン\]** をクリックします。  
  
## 参照  
 [方法: ステート マシン ワークフロー コンソール アプリケーションを作成する \(レガシ\)](../Topic/How%20to:%20Create%20State%20Machine%20Workflow%20Console%20Applications%20\(Legacy\).md)   
 [方法: ステート マシン ワークフロー ライブラリを作成する \(レガシ\)](../Topic/How%20to:%20Create%20a%20State%20Machine%20Workflow%20Library%20\(Legacy\).md)   
 [ステート マシン ワークフロー](http://go.microsoft.com/fwlink?LinkID=65016)   
 [StateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65083)   
 [StateInitializationActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65006)   
 [StateFinalizationActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65008)   
 [SetStateActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65082)   
 [EventDrivenActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65068)