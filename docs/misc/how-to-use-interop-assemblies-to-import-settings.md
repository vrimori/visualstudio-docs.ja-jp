---
title: "方法: 相互運用機能アセンブリを使用して設定をインポートする | Microsoft Docs"
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
  - "IDE 設定、相互運用機能アセンブリを使用したインポート"
  - "IDE、相互運用機能アセンブリを使用した設定のインポート"
  - "ユーザー設定 [Visual Studio SDK]、相互運用機能アセンブリを使用したインポート"
ms.assetid: 8a43dbe2-fdc0-471b-8235-3f489b77db0f
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# 方法: 相互運用機能アセンブリを使用して設定をインポートする
VSPackage は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) から設定をインポートできます。 IDE は VSPackage に実装された <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> インターフェイスを使用して、VSPackage の構成を取得する方法を決定します。  
  
> [!NOTE]
>  Managed Package Framework \(MPF\) には、Visual Studio 拡張機能の作成を支援する一連のマネージ クラスが用意されています。 MPF を使用してこのタスクを実行するには、「[設定のインポート](/visual-cpp/misc/importing-settings)」をご覧ください。  
  
### VSPackage で設定のインポートを実装するには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 設定メカニズムの基本的なサポートを実装します。  
  
    -   1 つ以上のカスタム設定ポイントを定義することで、設定メカニズムをサポートするように VSPackage を登録します。  
  
         詳細については、「[ユーザー設定のサポート](../extensibility/internals/support-for-user-settings.md)」を参照してください。  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> インターフェイスが VSPackage によって実装されることを宣言します。たとえば、次のようにします。  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   VSPackage に実装された <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> メソッドが、`IID_IVsUserSettings` で呼び出されるときに <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> インターフェイスを提供するようにします。 例:  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  設定情報を取得します。  
  
     設定情報の取得をサポートするために、VSPackage で <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> メソッドを実装する必要があります。  
  
     データを読み取るには、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> インターフェイスの VSPackage の実装が、IDE によって渡される最初の 2 つの引数、つまり、カスタム設定ポイントのカテゴリの GUID と、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> インターフェイスを使用する必要があります。  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> メソッドの VSPackage の実装は、渡されたカテゴリ GUID を確認し、状態を取得するための適切なメカニズムを選ばなければなりません。  
  
         次の例では、キー バインドの状態を取得する場合とは異なり、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> メソッドはコマンド バーの状態を取得するために異なる実装を呼び出します。  
  
    2.  VSPackage では、指定した <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> インターフェイスを使用して、設定ファイルにデータを取得する必要があります。  
  
        > [!NOTE]
        >  設定情報が [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] バージョンの機能として変更される場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> メソッドの VSPackage の実装は、IDE バージョンを確認するためにデータを読み取る前に <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> メソッドを使用しなければなりません。  
  
         インターフェイスには、設定ファイルの各種データ型を読み取るためのメソッドが備わっています。  
  
         `interface IVsSettingsReader : IUnknown`  
  
         `{`  
  
         `HRESULT ReadSettingString(WCHAR *pszSettingName, BSTR *pbstrSettingValue);`  
  
         `HRESULT ReadSettingLong(WCHAR *pszSettingName, long *plSettingValue);`  
  
         `HRESULT ReadSettingBoolean(WCHAR *pszSettingName, BOOL *pfSettingValue);`  
  
         `HRESULT ReadSettingAttribute(LPCOLESTR pszSettingName,LPCOLESTR pszAttributeName, BSTR *pbstrSettingValue);  //Internal use only`  
  
         `HRESULT ReadSettingBytes(WCHAR *pszSettingName, BYTE *pSettingValue, long *plDataLength, long lDataMax);`  
  
         `HRESULT ReadVersion(int *pnMajor, int *pnMinor, int *pnBuild);`  
  
         `HRESULT ReportError(WCHAR *pszError);`  
  
         `};`  
  
     設定ファイルではランダムなデータ アクセスがサポートされているため、設定の読み取りと書き込みの操作順序は重要ではありません。  
  
     この点については、コマンド バーの状態のエクスポートとインポート \(`ExportSettings_CommandBa`r および `ImportSettings_CommandBar`\) に関する以下の例に示されています。  
  
3.  取得したデータを検証します。  
  
     設定情報は XML ファイルに含まれていて、手動で編集できます。  
  
> [!IMPORTANT]
>  設定情報は、ディスク上で壊れたり、バージョン固有の設定が含まれていたり、悪意のある攻撃の手段として使用されたりする可能性があります。<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> メソッドによって返される各データ項目の有効性を検証しなければなりません。  
  
-   取得する設定を生成するために使用する [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] バージョンのサポートを確認するため、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> メソッドを呼び出してバージョンを取得します。  
  
-   インポートされるデータ要素が検証されていないことを IDE によってユーザーに通知させるため、VSPackage は <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A> メソッドを呼び出します。  
  
1.  設定情報を適用します。  
  
    1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> メソッドの実装では、IDE によって渡される 3 番目の引数の値を適用する必要があります。 サポートされる値は <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags> 列挙体のメンバーです。 詳細については、「<xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>」を参照してください。  
  
         次の例では、コマンド バーの設定のインポートを行うための実装 \(`ImportSettings_Commandbar`\) でこの引数の値を使用することによって、設定を適用して、既存の値を上書きするか、または追加更新するかを判別します。  
  
    2.  インポートされた設定を適用するときには、ライト スルー キャッシュ方式を実装する必要があります。  
  
         レジストリまたはファイル システムの状態情報は、IDE に設定が適用されるのと同時に更新しなければなりません。 これにより、構成の一貫性が確保され、マルチ インスタンスの IDE シナリオがサポートされます。  
  
2.  設定のインポートの処理方法を IDE に通知します。  
  
     インポートされた設定を適用するには再起動が必要な場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> メソッドの返された `pfRestartRequired` 引数を使用して IDE に通知します。  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> メソッドの VSPackage の実装が `true` を返すと、IDE の再起動を求める表示がユーザーに示されます。  
  
## 使用例  
 次の例では、設定データをインポートおよびエクスポートする方法を示します。  
  
```  
static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export and import //    Delegate to the right shell object based on the category GUID // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether to import as an additive operation or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## 参照  
 [方法: 相互運用機能アセンブリを使用して設定をエクスポートする](../misc/how-to-export-settings-by-using-interop-assemblies.md)   
 [ユーザー設定のサポート](../extensibility/internals/support-for-user-settings.md)   
 [ユーザー設定の拡張とオプション](../extensibility/extending-user-settings-and-options.md)   
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)