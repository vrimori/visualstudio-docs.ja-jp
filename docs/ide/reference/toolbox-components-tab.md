---
title: "ツールボックス、[コンポーネント] タブ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bb474e832f815453fd84ba35bc3680b961e17954
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="toolbox-components-tab"></a>ツールボックス、[コンポーネント] タブ
[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] および [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] のデザイナーに追加できるコンポーネントを表示します。 <xref:System.Messaging.MessageQueue> コンポーネントや <xref:System.Diagnostics.EventLog> コンポーネントなど、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に含まれている [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] コンポーネントに加え、独自のコンポーネントまたはサード パーティ製のコンポーネントをこのタブに追加できます。詳細については、「[How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)」 (方法: [ツールボックス] タブの操作) を参照してください。  
  
 このタブを表示するには、**[表示]** メニューで **[ツールボックス]** を選択します。 **ツールボックス**で、**[コンポーネント]** タブをクリックします。  
  
 **BackgroundWorker**  
 別の専用スレッドで操作を実行できる `System.ComponentModel.BackgroundWorker` コンポーネント インスタンスを作成します。  
  
 **DirectoryEntry**  
 Active Directory 階層内のノードまたはオブジェクトをカプセル化し、Active Directory サービス プロバイダーとやり取りするために使用できる <xref:System.DirectoryServices.DirectoryEntry> コンポーネント インスタンスを作成します。  
  
 **DirectorySearcher**  
 Active Directory に対してクエリを実行するために使用できる <xref:System.DirectoryServices.DirectorySearcher> コンポーネント インスタンスを作成します。  
  
 **ErrorProvider**  
 エンド ユーザーにフォーム上のコントロールに関連付けられているエラーがあることを示す、`System.Windows.Forms.ErrorProvider` コンポーネント インスタンスを作成します。  
  
 **EventLog**  
 ログへのイベントの書き込みおよびログ データの読み込みなど、システムおよびカスタム イベント ログとやり取りするために使用できる <xref:System.Diagnostics.EventLog> コンポーネント インスタンスを作成します。 詳細については、「[Introduction to the EventLog Component](http://msdn.microsoft.com/en-us/a2ba4f28-4b1a-435e-99ef-51b28e21f805)」 (EventLog コンポーネントの概要) を参照してください。  
  
 **FileSystemWatcher**  
 アクセス権がある任意のディレクトリまたはファイルへの変更を監視するために使用できる <xref:System.IO.FileSystemWatcher> コンポーネント インスタンスを作成します。 詳細については、「[How to: Configure FileSystemWatcher Component Instances](http://msdn.microsoft.com/en-us/2e628234-4951-4135-8a86-28b924070d50)」 (方法: FileSystemWatcher コンポーネント インスタンスの構成) を参照してください。  
  
 **HelpProvider**  
 コントロールのポップアップまたはオンライン ヘルプを提供する `System.Windows.Forms.HelpProvider` コンポーネント インスタンスを作成します。  
  
 **ImageList**  
 `System.Drawing.Image` オブジェクトのコレクションを管理するメソッドを提供する `System.Windows.Forms.ImageList` コンポーネント インスタンスを作成します。  
  
 **MessageQueue**  
 キューからメッセージを読み取る、メッセージをキューに書き込む、トランザクションの処理、およびキュー管理タスクの実行など、メッセージ キューとやり取りするために使用できる <xref:System.Messaging.MessageQueue> コンポーネント インスタンスを作成します。 詳細については、「[Using Messaging Components](http://msdn.microsoft.com/en-us/922dbac7-26f0-4e39-b666-ccfc184793d7)」 (メッセージング コンポーネントの使用) を参照してください。  
  
 **PerformanceCounter**  
 新しいカテゴリとインスタンスの作成、カウンターから値を読み取る、カウンター データに対して計算を実行するなど、Windows パフォーマンス カウンターとのやり取りに使用できる <xref:System.Diagnostics.PerformanceCounter> コンポーネント インスタンスを作成します。 詳細については、「[Monitoring Performance Thresholds](http://msdn.microsoft.com/en-us/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91)」(パフォーマンスのしきい値の監視) をご覧ください。  
  
 **Process**  
 システム上のプロセスに関連付けられているデータを停止、開始、および操作できる <xref:System.Diagnostics.Process> コンポーネント インスタンスを作成します。 詳細については、「[Monitoring and Managing Windows Processes](http://msdn.microsoft.com/en-us/a86bd4c1-b92c-49a0-8f32-61d67837b45e)」 (Windows プロセスの監視と管理) を参照してください。  
  
 **SerialPort**  
 同期 I/O とイベント ドリブン I/O のフレームワーク、ピンの状態とブレーク状態へのアクセス、およびシリアル ドライバーのプロパティへのアクセスを提供する `System.IO.Ports.SerialPort` コンポーネント インスタンスを作成します。  
  
 **ServiceController**  
 サービスの開始と停止やこれらのサービスへのコマンドの送信など、既存のサービスの操作に使用できる <xref:System.ServiceProcess.ServiceController> コンポーネント インスタンスを作成します。 詳細については、「[Monitoring Windows Services](http://msdn.microsoft.com/en-us/4542ee3f-e052-4cb9-8726-58e9420de222)」 (Windows サービスの監視) を参照してください。  
  
 **タイマー**  
 時間ベースの機能を Windows ベースのアプリケーションに追加するために使用できる <xref:System.Windows.Forms.Timer> コンポーネント インスタンスを作成します。 詳細については、「[Timer コンポーネント](/dotnet/framework/winforms/controls/timer-component-windows-forms)」を参照してください。  
  
> [!NOTE]
>  **ツールボックス**に追加できるシステム ベースの <xref:System.Timers.Timer> もあります。この <xref:System.Timers.Timer> は、サーバー アプリケーション用に最適化され、Windows フォーム <xref:System.Windows.Forms.Timer> は Windows フォームで使用するのに最も適しています。  
  
## <a name="see-also"></a>関連項目  
 [コンポーネントによるプログラミング](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)   
 [コンポーネント プログラミングのチュートリアル](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)   
 [ツールボックス](../../ide/reference/toolbox.md)   
 [[ツールボックス アイテムの選択] ダイアログ ボックス (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)