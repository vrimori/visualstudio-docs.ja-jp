---
title: '方法: ネイティブ コードのスレッド名を設定 |Microsoft Docs'
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: acddd39df0c91aeef5c425ffa67cb234d76d0473
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961352"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>方法: ネイティブ コードのスレッド名を設定する
スレッド名の設定は、Visual Studio のどのエディションでも実行できます。 スレッド名を設定すると、**[スレッド]** ウィンドウでスレッドを追跡する際に役立ちます。

## <a name="set-a-thread-name"></a>スレッド名を設定します。

`SetThreadName`関数は設定および実行中のコードにデバッガーがアタッチされている場合は、スレッドを表示するために役立ちます。 Visual Studio 2017 バージョン 15.6 以降、使える、 [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription)関数を設定し、スレッド名を表示します。

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

## <a name="set-a-thread-name-using-setthreadname"></a>SetThreadName を使用してスレッド名を設定します。

プログラムのスレッド名を設定するには、使用の`SetThreadName`関数は、次のコード例に示すようにします。 スレッド名はスレッドにコピーされるため、 `threadName` パラメーターのメモリは解放できます。  このメソッドは、例外ベースのメソッドの使用時に、デバッガーがアタッチされている場合にのみ機能例外ベースのアプローチを使用します。 ダンプやパフォーマンス分析ツールでは、このメソッドを使用して設定したスレッド名を利用できません。

次のコード例は、使用する方法を示しています`SetThreadName`:。

```C++
//  
// Usage: SetThreadName ((DWORD)-1, "MainThread");  
//  
#include <windows.h>  
const DWORD MS_VC_EXCEPTION = 0x406D1388;  
#pragma pack(push,8)  
typedef struct tagTHREADNAME_INFO  
{  
    DWORD dwType; // Must be 0x1000.  
    LPCSTR szName; // Pointer to name (in user addr space).  
    DWORD dwThreadID; // Thread ID (-1=caller thread).  
    DWORD dwFlags; // Reserved for future use, must be zero.  
 } THREADNAME_INFO;  
#pragma pack(pop)  
void SetThreadName(DWORD dwThreadID, const char* threadName) {  
    THREADNAME_INFO info;  
    info.dwType = 0x1000;  
    info.szName = threadName;  
    info.dwThreadID = dwThreadID;  
    info.dwFlags = 0;  
#pragma warning(push)  
#pragma warning(disable: 6320 6322)  
    __try{  
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);  
    }  
    __except (EXCEPTION_EXECUTE_HANDLER){  
    }  
#pragma warning(pop)  
}  
```  

## <a name="see-also"></a>「  
 [マルチスレッド アプリケーションのデバッグ](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)   
 [方法: マネージド コードのスレッド名を設定する](../debugger/how-to-set-a-thread-name-in-managed-code.md)