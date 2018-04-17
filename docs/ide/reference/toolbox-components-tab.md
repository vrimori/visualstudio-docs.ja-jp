---
title: ツールボックス、[コンポーネント] タブ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: aa91db706d7e1236162ef69e6fd31e791ed44dbb
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="toolbox-components-tab"></a>ツールボックス、[コンポーネント] タブ

Visual Basic および C# のデザイナーに追加できるコンポーネントを表示します。 <xref:System.Messaging.MessageQueue> コンポーネントや <xref:System.Diagnostics.EventLog> コンポーネントなど、Visual Studio に含まれている .NET Framework コンポーネントに加え、独自のコンポーネントまたはサード パーティ製のコンポーネントをこのタブに追加できます。
  
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
 ログへのイベントの書き込みおよびログ データの読み込みなど、システムおよびカスタム イベント ログとやり取りするために使用できる <xref:System.Diagnostics.EventLog> コンポーネント インスタンスを作成します。
  
 **FileSystemWatcher**  
 アクセス権がある任意のディレクトリまたはファイルへの変更を監視するために使用できる <xref:System.IO.FileSystemWatcher> コンポーネント インスタンスを作成します。
  
 **HelpProvider**  
 コントロールのポップアップまたはオンライン ヘルプを提供する `System.Windows.Forms.HelpProvider` コンポーネント インスタンスを作成します。  
  
 **ImageList**  
 `System.Drawing.Image` オブジェクトのコレクションを管理するメソッドを提供する `System.Windows.Forms.ImageList` コンポーネント インスタンスを作成します。  
  
 **MessageQueue**  
 キューからメッセージを読み取る、メッセージをキューに書き込む、トランザクションの処理、およびキュー管理タスクの実行など、メッセージ キューとやり取りするために使用できる <xref:System.Messaging.MessageQueue> コンポーネント インスタンスを作成します。

 **PerformanceCounter**  
 新しいカテゴリとインスタンスの作成、カウンターから値を読み取る、カウンター データに対して計算を実行するなど、Windows パフォーマンス カウンターとのやり取りに使用できる <xref:System.Diagnostics.PerformanceCounter> コンポーネント インスタンスを作成します。
  
 **Process**  
 システム上のプロセスに関連付けられているデータを停止、開始、および操作できる <xref:System.Diagnostics.Process> コンポーネント インスタンスを作成します。
  
 **SerialPort**  
 同期 I/O とイベント ドリブン I/O のフレームワーク、ピンの状態とブレーク状態へのアクセス、およびシリアル ドライバーのプロパティへのアクセスを提供する `System.IO.Ports.SerialPort` コンポーネント インスタンスを作成します。  
  
 **ServiceController**  
 サービスの開始と停止やこれらのサービスへのコマンドの送信など、既存のサービスの操作に使用できる <xref:System.ServiceProcess.ServiceController> コンポーネント インスタンスを作成します。
  
 **タイマー**  
 時間ベースの機能を Windows ベースのアプリケーションに追加するために使用できる <xref:System.Windows.Forms.Timer> コンポーネント インスタンスを作成します。 詳細については、「[Timer コンポーネント](/dotnet/framework/winforms/controls/timer-component-windows-forms)」を参照してください。  
  
> [!NOTE]
>  **ツールボックス**に追加できるシステム ベースの <xref:System.Timers.Timer> もあります。この <xref:System.Timers.Timer> は、サーバー アプリケーション用に最適化され、Windows フォーム <xref:System.Windows.Forms.Timer> は Windows フォームで使用するのに最も適しています。  
  
## <a name="see-also"></a>関連項目

[コンポーネントによるプログラミング](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
[コンポーネント プログラミングのチュートリアル](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)  
[ツールボックス](../../ide/reference/toolbox.md)