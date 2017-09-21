---
title: "式エバリュエーターを登録します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] の式の評価のデバッグ"
  - "式エバリュエーターを登録します。"
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 式エバリュエーターを登録します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 式エバリュエーター \(EE\) は、Windows COM 環境と Visual Studio の両方にクラス ファクトリとして自体を登録する必要があります。 EE は、デバッグ エンジン \(DE\) のアドレス空間またはエンティティが、EE をインスタンス化によって、Visual Studio アドレス空間のいずれかに挿入される可能性がありますので、DLL として実装されます。  
  
## マネージ コード式エバリュエーター  
 EE は、通常、VSIP プログラムへの呼び出しによって開始された COM 環境に自らを登録する DLL は、クラス ライブラリとして実装するマネージ コード **regpkg.exe**します。 COM 環境のレジストリ キーを作成する実際の処理は自動的に処理されます。  
  
 主なクラスのメソッドが付いて、 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, 、そのメソッドが、DLL が COM に登録されているときに呼び出されることを示す 多くの場合と呼ばれるこの登録方法 `RegisterClass`, 、Visual Studio で、DLL を登録するタスクを実行します。 対応する `UnregisterClass` \(でマークされた、 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>\) の効果を元に戻します `RegisterClass` DLL がアンインストールされます。  
  
 アンマネージ コードで記述され、EE の場合と同じのレジストリ エントリが作成されます。唯一の違いは、関数が存在しないヘルパーなど `SetEEMetric` の作業を実行します。 この登録\/登録解除プロセスの例は、次のようにはなります。  
  
### 例  
 この関数は、マネージ コード EE の登録し、Visual Studio での登録を解除自体を表示します。  
  
```c#  
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
  
## アンマネージ コードの式エバリュエーター  
 EE DLL に実装する、 `DllRegisterServer` COM 環境として Visual Studio に登録する関数。  
  
> [!NOTE]
>  MyCEE レジストリのコード例は、VSIP インストール EnVSDK\\MyCPkgs\\MyCEE の下にあるファイル dllentry.cpp に記載されています。  
  
### DLL のサーバー プロセス  
 EE、DLL サーバーを登録する: 時  
  
1.  クラス ファクトリを登録 `CLSID` 通常の COM 規則に従ってします。  
  
2.  ヘルパー関数を呼び出します `SetEEMetric` EE メトリックは、次の表に示すように、Visual Studio で登録します。 関数 `SetEEMetric` 以下で指定したメトリック dbgmetric.lib ライブラリの一部であるとします。 詳細については、「[デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)」を参照してください。  
  
    |メトリック|説明|  
    |-----------|--------|  
    |`metricCLSID`|`CLSID` EE クラス ファクトリの|  
    |`metricName`|表示可能な文字列として EE の名前|  
    |`metricLanguage`|EE は、言語の名前を評価するように設計|  
    |`metricEngine`|`GUID`この EE で動作するデバッグ エンジン \(DE\)|  
  
    > [!NOTE]
    >  `metricLanguage` `GUID` によって、名前がその言語を表すが、 `guidLang` 引数 `SetEEMetric` 言語を選択します。 コンパイラは、デバッグ情報ファイルを生成するときは出力するように、適切な `guidLang` デを使用するには、どの EE が認識できるようにします。 デは、この言語のシンボル プロバイダーを確認する一般 `GUID`, 、デバッグ情報ファイルに格納されました。  
  
3.  HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ の下にキーを作成することで、Visual Studio で登録*X.Y*, ここで、 *X.Y* に登録する Visual Studio のバージョンです。  
  
### 例  
 この関数は、アンマネージ コード \(C\+\+\) EE の登録および自体で Visual Studio の登録を解除するしくみを示しています。  
  
```cpp#  
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
  
## 参照  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)