---
title: Status | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: debc70294bf0b513f22ed1cc06b9f0790da7b778
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="status"></a>Status
VSPerfCmd.exe の **Status** オプションでは、プロファイラーの状態、および現在プロファイルを実行中の任意のプロセスに関する情報を表示します。  
  
 コマンド ラインで指定するオプションは **Status** オプションのみにする必要があります。 状態を表示するには、VSPerfCmd.exe の **Start** オプションを使用してプロファイラーを初期化しておく必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>パラメーター  
 なし  
  
## <a name="remarks"></a>コメント  
 **Status** オプションでは、プロファイラーに関して、次の状態情報を表示します。  
  
 **出力ファイル名**  
 現在のプロファイラー データ ファイルのパスとファイル名。  
  
 **コレクション モード**  
 SAMPLE または TRACE  
  
 **最大プロセス**  
 同時にプロファイルできる最大プロセス数と、現在アクティブなプロセス数。  
  
 **最大スレッド**  
 同時にプロファイルできる最大スレッド数。  
  
 **バッファー数**  
 プロファイル データの書き込み専用のメモリ バッファー数。  
  
 **バッファー サイズ**  
 メモリ バッファーのサイズ (バイト単位)。  
  
 **Status** オプションでは、現在プロファイルされている各プロセスに関して、次の状態情報を表示します。  
  
 **Process**  
 プロファイルされているプロセスの名前。  
  
 **プロセス ID**  
 プロセスのシステム ID。  
  
 **Num スレッド**  
 現在実行中のスレッド数。  
  
 **開始/停止数**  
 このプロセスに対するデータ収集を制御するプライマリ内部プロファイラー カウント。 データを収集するには、このカウントが 1 である必要があります。 開始/停止数は、プロファイラー API、および VSPerfCmd オプションである **GlobalOn**、**GlobalOff**、**ProcessOn**、**ProcessOff**、**ThreadOn**、および **ThreadOff** によって操作できます。  
  
 **保留/再開数**  
 このプロセスに対するデータ収集を制御するセカンダリ内部プロファイラー カウント。 データを収集するには、このカウントが 0 以下である必要があります。 **保留/再開**数は、プロファイラー API によってのみ操作できます。  
  
 **監視するアクセス権を伴うユーザー**  
 プロファイラーにアクセスできるユーザーの名前を一覧表示します。 VSPerfCmd.exe の **Admin** オプションを使用して、追加ユーザーにアクセスを許可できます。  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [プロファイリング (サービスの)](../profiling/command-line-profiling-of-services.md)