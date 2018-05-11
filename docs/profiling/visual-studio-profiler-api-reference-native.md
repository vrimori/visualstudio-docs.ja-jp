---
title: Visual Studio プロファイラー API リファレンス (ネイティブ) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: d79399ebea9fd5dedd645b148910d6a4ced47902
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="visual-studio-profiler-api-reference-native"></a>Visual Studio プロファイラー API リファレンス (ネイティブ)
Visual Studio プロファイラー API を使用すると、収集データの量をプログラムで制御したり、タイムスタンプとプロファイルの両方のマークをプロファイル時に挿入したりできます。 ネイティブ API を使用するには、VSPerf.h ヘッダー ファイルをインクルードし、VSPerf.lib をプロジェクトに追加する必要があります。  
  
> [!NOTE]
>  既定では、VSPerf.h と VSPerf.lib は PerfSDK という名前のフォルダーにあります。 たとえば、\<ドライブ>:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\PerfSDK ディレクトリなどです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [CommentMarkAtProfile](../profiling/commentmarkatprofile.md)  
  
 [CommentMarkProfile](../profiling/commentmarkprofile.md)  
  
 [MarkProfile](../profiling/markprofile.md)  
  
 [NameProfile](../profiling/nameprofile.md)  
  
 [ResumeProfile](../profiling/resumeprofile.md)  
  
 [StartProfile](../profiling/startprofile.md)  
  
 [StopProfile](../profiling/stopprofile.md)  
  
 [SuspendProfile](../profiling/suspendprofile.md)  
  
 [PROFILE_CURRENTID](../profiling/profile-currentid.md)  
  
## <a name="see-also"></a>参照  
 [プロファイリング ツールの API](../profiling/profiling-tools-apis.md)   
 [チュートリアル : プロファイラー API の使用](../profiling/walkthrough-using-profiler-apis.md)
