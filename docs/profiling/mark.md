---
title: Mark | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 952d5c726090aabbc4fe550f64696bcce7a3f784
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940077"
---
# <a name="mark"></a>Mark
*VSPerfCmd.exe* の **Mark** オプションは、プロファイル データ ファイルに指定した情報を挿入します。 マークは個別の VSPerfReport レポートまたはプロファイラー UI のマーク レポート ビューに一覧表示できます。 **Mark** を使用して、レポートおよびビュー フィルターの開始点と終了点を指定できます。  
  
 コマンド ラインで指定するオプションは **Mark** オプションのみにする必要があります。  
  
## <a name="syntax"></a>構文  
  
```cmd  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `MarkID`  
 プロファイラー ビューおよびレポートにマーク ID として一覧表示される、ユーザー定義の整数。 `MarkID` は一意である必要はありません。  
  
 `MarkName`  
 (省略可能) プロファイラー ビューおよびレポートにマーク名として一覧表示される、ユーザー定義の文字列。 `MarkName` が指定されていない場合、マーク一覧のマーク名フィールドは空になります。 スペースやスラッシュ ("/") を含む文字列は引用符で囲みます。  
  
## <a name="example"></a>例  
 この例では、ID が 123 でマーク名が "TestMark" というマークを挿入します。  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>関連項目  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [サービスのプロファイリング](../profiling/command-line-profiling-of-services.md)