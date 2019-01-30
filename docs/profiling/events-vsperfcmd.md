---
title: Events (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48957b7078f8348f4ac1489267b603992e04a56a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965763"
---
# <a name="events-vsperfcmd"></a>Events (VSPerfCmd)
*VSPerfCmd.exe* **Events** オプションは、Windows イベント トレーシング (ETW) のログ記録を制御します。 ETW データは、プロファイラー データ ファイルとは別の .etl ファイルに保存されます。 このデータは、[VSPerfReport](../profiling/vsperfreport.md) /summary:etw コマンドを利用し、レポートで表示できます。  
  
 **Events** オプションは、VSPerfCmd **Shutdown** コマンドが呼び出され、プロファイリングを停止する前にいつでも呼び出すことができます。  
  
## <a name="syntax"></a>構文  
  
```cmd  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>パラメーター  
 **On**&#124;**Off**  
 イベント データの収集を開始または停止します。  
  
 `Guid`  
 プロバイダー コントロールの GUID。  
  
 `ProviderName`  
 Windows Management Instrumentation (WMI) に登録されているプロバイダーの名前。  
  
 `Flags`  
 イベント プロバイダーによって定義され、先頭に "0x" が付く 16 進数のフラグ値。  
  
 `Level`  
 収集されるデータの量を指定します。 `Level` はイベント プロバイダーによって定義されます。  
  
 **Events** オプションは、プロバイダー名として次のカーネル キーワードを理解します。  
  
 **Process**  
 プロセス イベント  
  
 **スレッド**  
 スレッド イベント  
  
 **イメージ**  
 イメージのロードとアンロード イベント  
  
 **Disk**  
 ディスク I/O イベント  
  
 **ファイル**  
 ファイル I/O イベント  
  
 **Hardfault**  
 ハード ページ フォールト  
  
 **Pagefault**  
 ソフト ページ フォールト  
  
 **Network**  
 ネットワーク イベント  
  
 **Registry**  
 レジストリ アクセス イベント  
  
 カーネル プロバイダーのみを有効にできます。 モニターがシャットダウンするまで、無効にできません。そのフラグを変更することもできません。  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  CLR ETW イベントが有効になっていると、追加のスタートアップ データがトレース ビュー レポートでも集められます。 スタートアップ イベントがレポートに表示されないようにするには、次のコマンドを使用します。  
  
```cmd  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  スタートアップ イベントを除外しない場合、スタートアップ イベントはマネージド オブジェクト フォーマット (MOF) ファイルに一覧表示されないため、レポートに GUID として表示されます。 詳細については、Microsoft Web サイトの「[Sample Managed Object Format (MOF) File](http://go.microsoft.com/fwlink/?linkid=37118)」 (マネージド オブジェクト フォーマット (MOF) ファイルのサンプル) を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [サービスのプロファイリング](../profiling/command-line-profiling-of-services.md)