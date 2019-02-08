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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 56ae83f41a53ad35c1bec0fd4e0d256f0a8575d7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926255"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>方法: ネイティブ コードのスレッド名を設定する
スレッド名の設定は、Visual Studio のどのエディションでも実行できます。 関心のあるスレッドを識別するために便利ですがスレッドの名前を付け、**スレッド**ウィンドウの実行中のプロセスをデバッグするときにします。 スレッドの関係という名前を持つも役に立ちますさまざまなツールを使用してキャプチャするパフォーマンスの分析とクラッシュ ダンプの検査を使用して事後分析のデバッグを実行する場合。

## <a name="ways-to-set-a-thread-name"></a>スレッド名を設定する方法

スレッド名を設定する 2 つの方法はあります。 使用して 1 つ目は、 [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription)関数。 2 つ目は、Visual Studio デバッガーがプロセスにアタッチされている間は、特定の例外をスローすることです。 各手法では、利点と注意事項があります。

いることに注意が_両方_動作するメカニズムは相互に依存しないため、必要な場合は、方法を同時に使用できます。

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>使用してスレッド名を設定します。 `SetThreadDescription`

利点:
 * SetThreadDescription が呼び出される時点で、デバッガーをプロセスにアタッチされたかどうかに関係なく、Visual Studio でデバッグするときに、スレッド名が表示されます。
 * 事後分析のデバッグを Visual Studio でのクラッシュ ダンプを読み込んで実行するときに、スレッド名が表示されます。
 * スレッド名などの他のツールを使用する場合にも表示、 [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools)デバッガーと[Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer)パフォーマンス アナライザーです。

注意事項:
 * スレッド名は、Visual Studio 2017 バージョン 15.6 で表示されている以降のみです。
 * 事後分析、クラッシュのデバッグ ダンプ ファイル、ときにスレッド名は、クラッシュは、Windows 10 バージョン 1607 を Windows Server 2016 または Windows の以降のバージョンで作成した場合は、表示のみ。
 
*例:*

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>例外をスローして、スレッド名を設定します。

プログラムのスレッド名を設定する別の方法では、特別に構成された例外をスローして、目的のスレッド名を Visual Studio デバッガーに通信するためにします。 

利点:
 * Visual Studio のすべてのバージョンで動作します。

注意事項:
 * 例外ベースのメソッドの使用時に、デバッガーがアタッチされている場合にのみ機能します。 
 * ダンプやパフォーマンス分析ツールでは、スレッド名がこのメソッドを使用して設定を使用できません。
 
*例:*

`SetThreadName`以下の関数は、この例外ベースのアプローチを示します。 スレッドにスレッド名を自動的にコピーすることに注意してください。 ように用のメモリ、`threadName`パラメーターは、後にリリースされることができます、`SetThreadName`呼び出しが完了しました。 

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

## <a name="see-also"></a>関連項目
 [マルチスレッド アプリケーションのデバッグ](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)   
 [方法: マネージド コードのスレッド名を設定する](../debugger/how-to-set-a-thread-name-in-managed-code.md)
