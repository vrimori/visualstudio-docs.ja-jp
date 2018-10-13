---
title: 式エバリュエーターの登録 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c045f8f50e945627e0f6d8f01c07c47a511cd2b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210705"
---
# <a name="registering-an-expression-evaluator"></a>式エバリュエーターの登録
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 式エバリュエーター (EE) は、Windows COM 環境と Visual Studio の両方でクラス ファクトリとして自体を登録する必要があります。 EE は、これは、デバッグ エンジン (DE) のアドレス空間またはエンティティが、EE をインスタンス化によって、Visual Studio のアドレス空間のいずれかに挿入することがありますように DLL として実装されます。  
  
## <a name="managed-code-expression-evaluator"></a>マネージ コードの式エバリュエーター  
 EE が自ら COM 環境は、通常、VSIP プログラムへの呼び出しにより起動を登録する DLL は、クラス ライブラリとして実装されているマネージ コード**regpkg.exe**します。 COM 環境のレジストリ キーの書き込みの実際のプロセスが自動的に処理されます。  
  
 メイン クラスのメソッドが付いて、<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>メソッドが、DLL が COM に登録されているときに呼び出されることを示す この登録メソッドは、多くの場合と呼ばれる`RegisterClass`、Visual Studio で DLL を登録するためのタスクを実行します。 対応する`UnregisterClass`(でマークされた、 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>) の効果を元に戻します`RegisterClass`DLL がアンインストールされます。  
  
 アンマネージ コードで記述された、EE の場合と同じのレジストリ エントリが作成されます。唯一の違いがあるないヘルパー関数など`SetEEMetric`に仕事ができます。 この登録または登録解除プロセスの例のようになります。  
  
### <a name="example"></a>例  
 この関数は、マネージ コード EE の登録し、Visual Studio を使用したそのものの登録を解除を示しています。  
  
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
 EE DLL に実装する、 `DllRegisterServer` COM 環境として Visual Studio に登録する関数。  
  
> [!NOTE]
>  MyCEE コード サンプル レジストリ コードは、VSIP インストール EnVSDK\MyCPkgs\MyCEE の下にあるファイル dllentry.cpp で確認できます。  
  
### <a name="dll-server-process"></a>サーバー プロセスの DLL  
 EE、DLL サーバーを登録する: 場合  
  
1.  クラス ファクトリを登録します`CLSID`通常の COM 規則に従ってします。  
  
2.  ヘルパー関数を呼び出す`SetEEMetric`EE メトリックが、次の表に示すように Visual Studio で登録します。 関数は、`SetEEMetric`以下で指定したメトリック dbgmetric.lib ライブラリの一部であるとします。 参照してください[デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)詳細についてはします。  
  
    |メトリック|説明|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` EE クラス ファクトリの|  
    |`metricName`|表示可能な文字列として EE の名前|  
    |`metricLanguage`|EE は言語の名前を評価するように設計|  
    |`metricEngine`|`GUID`この EE と連携するデバッグ エンジン (DE)|  
  
    > [!NOTE]
    >  `metricLanguage``GUID`によって名、言語を識別しますが、`guidLang`への引数`SetEEMetric`する言語を選択します。 適切な書き込む必要がありますが、コンパイラは、デバッグ情報ファイルを生成するとき`guidLang`DE が使用するには、どの EE を認識できるようにします。 デは、この言語のシンボル プロバイダーを要求する通常`GUID`、デバッグ情報ファイルに格納されています。  
  
3.  Hkey_local_machine \software\microsoft\visualstudio の下にキーを作成して Visual Studio を使用した登録\\*X.Y*ここで、 *X.Y*を登録する Visual Studio のバージョンです。  
  
### <a name="example"></a>例  
 この関数は、アンマネージ コード (C++) EE の登録し、Visual Studio を使用した登録を解除します自体を表示します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [CLR の式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [デバッグ用の SDK ヘルパー](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

