---
title: 式エバリュエーターを登録する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a34278ecca071c31e62ff4e405e9d7ada112d425
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129564"
---
# <a name="registering-an-expression-evaluator"></a>式エバリュエーターを登録します。
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 式エバリュエーター (EE) は、Windows COM 環境と Visual Studio の両方でクラス ファクトリとして自体を登録する必要があります。 EE は、デバッグ エンジン (DE) のアドレス空間またはエンティティに応じて EE をインスタンス化、Visual Studio のアドレス空間のいずれかに挿入される可能性がありますように DLL として実装されます。  
  
## <a name="managed-code-expression-evaluator"></a>マネージ コード式エバリュエーター  
 EE は、通常 VSIP プログラムへの呼び出しによって開始された COM 環境に自らを登録する DLL は、クラス ライブラリとして実装するマネージ コード**regpkg.exe**です。 COM 環境のレジストリ キーに書き込む実際の処理が自動的に処理されます。  
  
 主要なクラスのメソッドが付いて、 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>、そのメソッドが、DLL が COM に登録されているときに呼び出されることを示す この登録メソッドは多くの場合、 `RegisterClass`、Visual Studio で、DLL を登録する次のタスクを実行します。 対応する`UnregisterClass`(でマークされた、 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>) の効果を元に戻します`RegisterClass`DLL がアンインストールされるときにします。  
  
 アンマネージ コードで記述された、EE の場合と同じのレジストリ エントリが作成されます。唯一の違いは、関数が存在しないヘルパーなど`SetEEMetric`の作業を行う。 この登録/登録解除のプロセスの例は、次のようになります。  
  
### <a name="example"></a>例  
 この関数は、マネージ コード EE が登録および Visual Studio でそれ自体の登録を解除するしくみを示しています。  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>アンマネージ コードの式エバリュエーター  
 EE DLL に実装する、 `DllRegisterServer` COM 環境として Visual Studio の登録をする関数。  
  
> [!NOTE]
>  MyCEE レジストリのコード例は、VSIP インストール EnVSDK\MyCPkgs\MyCEE の下にあるファイル dllentry.cpp に含まれています。  
  
### <a name="dll-server-process"></a>DLL のサーバー プロセス  
 EE、DLL サーバーを登録する: 場合  
  
1.  そのクラス ファクトリを登録`CLSID`通常の COM 規則に従ってします。  
  
2.  ヘルパー関数を呼び出す`SetEEMetric`EE メトリックは、次の表に示すように、Visual Studio に登録します。 関数は、`SetEEMetric`以下で指定したメトリック dbgmetric.lib ライブラリの一部であるとします。 参照してください[をデバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)詳細についてはします。  
  
    |メトリック|説明|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` EE クラス ファクトリ|  
    |`metricName`|表示可能な文字列として EE の名前|  
    |`metricLanguage`|EE は、言語の名前は、評価するよう設計されています|  
    |`metricEngine`|`GUID`この EE で動作するデバッグ エンジン (DE)|  
  
    > [!NOTE]
    >  `metricLanguage``GUID`言語を名前によって識別が、`guidLang`引数`SetEEMetric`言語を選択します。 コンパイラは、デバッグ情報ファイルを生成するときは出力するように、適切な`guidLang`デを使用するには、どの EE が認識できるようにします。 デはこの言語のシンボル プロバイダーを要求する通常`GUID`、デバッグ情報ファイルに格納されています。  
  
3.  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio の下にキーを作成することで、Visual Studio で登録\\*X.Y*ここで、 *X.Y*に登録する Visual Studio のバージョンです。  
  
### <a name="example"></a>例  
 この関数は、アンマネージ コード (C++) EE が登録および Visual Studio でそれ自体の登録を解除するしくみを示しています。  
  
```cpp  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)