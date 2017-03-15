---
title: "方法: 相互運用機能アセンブリを使用して設定をエクスポートする | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE 設定、相互運用機能アセンブリを使用したエクスポート"
  - "ユーザー設定 [Visual Studio SDK]、相互運用機能アセンブリを使用したエクスポート"
  - "IDE、相互運用機能アセンブリを使用した設定のエクスポート"
ms.assetid: d470d4f9-3006-40c3-99db-21abcd5003b8
caps.latest.revision: 23
caps.handback.revision: 23
manager: "douge"
---
# 方法: 相互運用機能アセンブリを使用して設定をエクスポートする
VSPackage は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) から設定をエクスポートできます。 IDE では、VSPackage に実装された <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> インターフェイスを使用します。 このパッケージに <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> インターフェイスも用意されている場合は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> インターフェイスを使用して VSPackage の構成の保存方法が決定されます。  
  
> [!NOTE]
>  Managed Package Framework \(MPF\) には、Visual Studio 拡張機能の作成を支援する一連のマネージ クラスが用意されています。 MPF を使用してこのタスクを実行するには、「[設定のエクスポート](../misc/exporting-settings.md)」を参照してください。  
  
### VSPackage で設定のエクスポートを実装するには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 設定メカニズムの基本的なサポートを実装します。  
  
    -   1 つ以上のカスタム設定ポイントを定義することで、設定メカニズムをサポートするように VSPackage を登録します。  
  
         詳細については、「[ユーザー設定のサポート](../extensibility/internals/support-for-user-settings.md)」を参照してください。  
  
    -   VSPackage が <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> を実装することを宣言します。 必要に応じて、VSPackage では <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> インターフェイスも実装できます。 例:  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   VSPackage に実装された <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> メソッドでは、`IID_IVsUserSettings` で呼び出すときに <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> インターフェイスを指定するようになっていることを確認します。  
  
         必要に応じて、`QueryInterface` では `IID_IVsUserSettingsQuery` インターフェイスで呼び出すときに <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> インターフェイスを指定することもできます。  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  必要に応じて、特定の設定をエクスポートする必要があることを IDE で警告します。  
  
     VSPackage では、カスタム設定ポイントの状態が定義する設定を条件付きで保存することもできます。 たとえば、ユーザーが設定の保存を明示的に指定した場合にのみ保存します。  
  
     この場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> インターフェイスを実装する必要があります。  
  
     VSPackage が <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery> を実装していない場合は、設定のエクスポート中にすべての状態情報が保存されます。  
  
     VSPackage では、複数のカスタム設定ポイント \(設定カテゴリ\) をサポートできます。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettingsQuery.NeedExport%2A> メソッドの実装では、特定のグループの設定を保存する必要があるかどうかを判断するために、指定したカスタム設定ポイントの GUID または設定カテゴリの引数を確認する必要があります。  
  
     次の例では、VSPackage はコマンド バーの状態を保存するように常に要求しますが、キー バインドの状態を保存するように要求するのはフラグが設定されている場合だけです。  
  
3.  設定データを設定ファイルに書き込みます。  
  
     エクスポートの設定をサポートするには、VSPackage に常に <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> メソッドを実装する必要があります。  
  
     この実装では、IDE から渡される引数、カスタム設定ポイントのカテゴリの GUID、および <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> インターフェイスを処理する必要があります。  
  
    1.  VSPackage では、複数のカスタム設定ポイント \(設定カテゴリ\) をサポートできます。 次の例では、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> メソッドはキー バインドの状態を保持する場合とは異なる実装を呼び出して、コマンド バーの状態を保持しています。  
  
    2.  VSPackage では、指定した <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> インターフェイスを使用して、設定ファイルにデータを保存する必要があります。  
  
         `interface IVsSettingsWriter : IUnknown`  
  
         `{`  
  
         `HRESULT WriteSettingString( LPCOLESTR pszSettingName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingLong( LPCOLESTR pszSettingName, long lSettingValue);`  
  
         `HRESULT WriteSettingBoolean( LPCOLESTR pszSettingName, BOOL fSettingValue);`  
  
         `HRESULT WriteSettingBytes( LPCOLESTR pszSettingName, BYTE *pSettingValue, long lDataLength);`  
  
         `HRESULT WriteSettingAttribute( LPCOLESTR pszSettingName, LPCOLESTR pszAttributeName, LPCOLESTR pszSettingValue);`  
  
         `HRESULT WriteSettingXml( IUnknown *pIXMLDOMNode);`  
  
         `HRESULT WriteSettingXmlFromString( LPCOLESTR szXML);`  
  
         `HRESULT ReportError( LPCOLESTR pszError, VSSETTINGSERRORTYPES dwErrorType);`  
  
         `};`  
  
         <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> インターフェイスに指定された `pszSettingName` 引数の値により、設定のカテゴリ内に保存されている各データ要素を一意に識別する必要があります。  
  
        > [!NOTE]
        >  名前は、カスタム設定ポイント内で一意である必要があります。IDE では、その GUID と `pszSettingName` の値を使用して、保存した各設定を識別しているからです。 複数の <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> メソッドを同じ `pszSettingName` の値で呼び出した場合、設定ファイル内の元の値が上書きされます。  
  
         設定ファイルでは、ランダムなデータ アクセスをサポートしています。 したがって、設定の読み書き操作は重要ではありません。  
  
         以下の例では、これをエクスポートとインポートのコマンド バーの状態の実装 \(`ExportSettings_CommandBa`r と `ImportSettings_CommandBar`\) で示します。  
  
         この実装では、サポートされている 4 つの形式のいずれかにデータをマッピングできる場合、書き込めるデータの量と種類に制限はありません。  
  
        > [!NOTE]
        >  設定 API は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> 実装に透過的な方法でデータを明示的に書き込むだけでなく、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] バージョン情報も保存します。 保存した設定は、設定のインポート時に、その設定を生成した IDE のバージョンに対して比較できます。  
  
## 使用例  
 次の例では、設定データをインポートおよびエクスポートする方法を示します。  
  
```  
// -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export. //    Delegate to the right shell object based on the category GUID. // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on // the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to treat import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning, these settings should immediately //             be applied to your personal settings store, //             whether in the registry or the file system. // This write-through cache methodology is essential to to work //             in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether import can be treated as an additive // operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: Before returning, these settings should immediately //             be applied to your personal settings //             store, whether in the registry or the file system. // This write-through cache methodology is essential to allow us //             to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## 参照  
 [ユーザー設定のサポート](../extensibility/internals/support-for-user-settings.md)   
 [ユーザー設定の拡張とオプション](../extensibility/extending-user-settings-and-options.md)   
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [方法: 相互運用機能アセンブリを使用して設定をインポートする](../misc/how-to-use-interop-assemblies-to-import-settings.md)