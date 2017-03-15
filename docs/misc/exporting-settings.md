---
title: "設定のエクスポート | Microsoft Docs"
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
  - "IDE、Managed Package Framework を使用した設定のエクスポート"
  - "Managed Package Framework、環境設定のエクスポート"
  - "ユーザー設定 [Visual Studio SDK]、Managed Package Framework を使用したエクスポート"
  - "IDE 設定、Managed Package Framework を使用したエクスポート"
ms.assetid: cb3ddb38-4e75-4f05-a83a-8396345bc36c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# 設定のエクスポート
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の統合開発環境では \(IDE\)VSPackage の状態を保存する VSPackage の実装のサポートとして登録されるクラスと <xref:Microsoft.VisualStudio.Shell.IProfileManager> のインターフェイスを実装するクラスを使用します。  
  
 IDE がサポートするために <xref:Microsoft.VisualStudio.Shell.IProfileManager> のインターフェイスを実装するクラスのインスタンスを作成するため <xref:Microsoft.VisualStudio.Shell.IProfileManager> は独立したクラスで実装する必要があります。  
  
> [!NOTE]
>  このクラスの <xref:Microsoft.VisualStudio.Shell.IProfileManager> を実装 <xref:Microsoft.VisualStudio.Shell.Package> 実行しないでください。  
  
### 設定のエクスポートを実行するには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の設定を実装するクラスを宣言します。  
  
     クラスを <xref:Microsoft.VisualStudio.Shell.IProfileManager> インターフェイスの実装として宣言しGUIDを指定します。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.IProfileManager> を実装するクラスは<xref:System.ComponentModel.IComponent> を実装する必要があります。  これは <xref:System.ComponentModel.Component> からクラスを派生させてできます。  
  
     次に例を示します。  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  設定を実装するクラスが正しい状態情報を取得することを確認します。  この手順ではVSPackage に固有ではオートメーションの状態を取得したりレジストリ キーを呼び出すかVSPackage を呼び出すことが必要になる場合があります。  
  
     通常次の例のようにVSPackage の状態情報を検証しステージング サーバーに <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> のメソッドの実装を使用します。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> のメソッドはIDE でサポートする VSPackage を初期化するときに呼び出されます。  
  
     この場合<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> のメソッドの実装はこれらの機能を実行します :  
  
    -   レジストリに保存される VSPackage の現在の構成設定と情報の状態情報へのアクセスを取得します。  
  
        ```vb#  
        Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
        Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
        Dim rootKey As RegistryKey = package.UserRegistryRoot  
        ```  
  
        ```c#  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        Package package = GetService(typeof(Package)) as Package;  
        RegistryKey rootKey = package.UserRegistryRoot;  
        ```  
  
    -   値によって VSPackage で `MakeCurrentSettingTheDefault` のメソッドによって更新 VSPackage の現在の状態を使用してレジストリ設定またはレジストリ設定によって返される状態。  
  
        ```vb#  
        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
        Else   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
        }else{  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
        }  
        ```  
  
         簡略化のためにレジストリに格納されている既定値に `MakeCurrentSettingsTheDefault` のメソッド `true` が現在の状態にリセットしない場合は必ずこの例で。  
  
3.  設定の状態を実装するクラスがディスクに永続化することを確認します。  
  
     設定をディスク ファイルのステータス情報の実際の書き込みは <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> のメソッド実装によって常に実行する必要があります。  ライター設定操作の仕様は実装によって異なります。  
  
     ただしクラスは状態情報へのアクセスを取得し設定ファイルにデータを格納するために <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> の指定されたインターフェイスを使用する必要があります。  
  
     通常次の例のように<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> のメソッドの実装は状態情報を検証しません。  検証は <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> のメソッドで実行されます。  代わりに実装は状態情報へのアクセスを取得し文字列データとしてこの場合書き込みます。  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        ' Information is stored in a StateObject   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
        writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
    End If  
  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
    if (mySvc != null) {  
      // Information is stored in a StateObject  
      StateObject myState = mySvc.MyPackage.packageState;  
     writer.WriteSettingString(   
                                "PbrsAlpha",   
                                (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
      writer.WriteSettingString(   
                                "PbrsShowDesc",   
                                (myState.HelpVisible ? "1" : "0"));  
    }  
    ```  
  
     実装の詳細は次のとおりです。:  
  
    -   明示的に <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> のメソッドの実装に書き込まれ透明なデータに加えて構成 API は[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョン情報を格納します。  したがって保存した設定は構成のインポート時に生成した IDE のバージョンに対して比較できます。  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> インターフェイスのメソッドに渡される `pszSettingName` の引数の値は設定カテゴリに格納されている各データ要素を識別する必要があります。  
  
        > [!NOTE]
        >  名前を実装するクラスのスコープ内でのみ一意である必要があります。  IDE では保存された設定を指定するに `pszSettingName` の設定と値を実装するクラスの GUID を使用します。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> の複数のメソッドが `pszSettingName` の同じ値を持つ呼び出すと元の値は設定ファイルで上書きされます。  
  
    -   設定はサポートのランダムなデータ アクセスを許可します。読み取り書き込み操作の順序は重要ではありません。  次の例では<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> のメソッドの実装のライターの操作の順序は <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> のメソッドの読み取り操作のオブジェクトです。  
  
    -   実装が 4 台のサポートされる形式の 1 にマップできますがどのようなデータにデータを書き込むことができるの大きさや制限はありません。  
  
        > [!NOTE]
        >  <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> と <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> のメソッドを分業は実装に依存しは任意です。  たとえば実装は <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> のメソッドの実装を使用して <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> のメソッドで発生したすべてのレジストリまたはの状態にクエリを追加することにより記述することもできます。  
  
4.  VSPackage に登録してサポートを提供するように構成のクラスを実装します。  
  
     このクラスの <xref:System.Type> を使用してVSPackage <xref:Microsoft.VisualStudio.Shell.Package> の実装に実装 <xref:Microsoft.VisualStudio.Shell.IProfileManager> 構築 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> のインスタンスを適用します。  
  
    ```vb#  
    <ProvideProfile(GetType(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, False)> _   
    <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Class MyPackage   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
    [ProvideProfile(typeof(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, false)]  
    [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    class MyPackage: Package   
    ```  
  
     この場合属性は `MyPackageProfileManager` のクラスがに設定 `MyPackage` のクラスを実装すること IDE に通知します。  レジストリのカスタム指して点が HKLM \\ SOFTWARE \\ Microsoft \\  *バージョン*  が [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョン \(たとえば10.0 である  *バージョン* \\ \\ VisualStudio \\ UserSettings CoreUI\_MyPackage の下に作成されます。  
  
     詳細については、「[ユーザー設定のサポート](../extensibility/internals/support-for-user-settings.md)」および「<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>」を参照してください。  
  
## 使用例  
 次の例はクラスの <xref:Microsoft.VisualStudio.Shell.IProfileManager> を実行します。  
  
```vb#  
Imports System   
Imports System.Runtime.InteropServices   
Imports Microsoft.VisualStudio.Shell   
Imports Microsoft.VisualStudio.Shell.Interop   
Imports Microsoft.Win32   
Imports myPackageNameSpace   
Namespace myProfileManagerNameSpace  
  
    <Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class MyPackageProfileManager   
        Inherits System.ComponentModel.Component   
        Implements IProfileManager   
        Friend Const m_supportVer As Integer = 8   
        Public Sub SaveSettingsToXml(ByVal writer As IVsSettingsWriter)   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
            If mySvc IsNot Nothing Then   
                ' Information is stored in a StateObject.   
                Dim myState As StateObject = mySvc.MyPackage.packageState   
                writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
                writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromXml(ByVal reader As IVsSettingsReader)   
  
            Dim pnMajor As Integer, pnMinor As Integer, pnBuild As Integer   
            ' First, check if data is obtained from the correct major version   
            reader.ReadVersion(pnMajor, pnMinor, pnBuild)   
            If pnMajor <> m_supportVer Then   
                reader.ReportError("Unsupported Version")   
            Else   
                Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
                If mySvc IsNot Nothing Then   
                    Dim value As String   
                    Dim myState As StateObject = mySvc.MyPackage.packageState   
                    reader.ReadSettingString("PbrsShowDesc", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Help Visibility Setting")   
                    Else   
                        myState.HelpVisible = Not value.Equals("0")   
                    End If   
                    reader.ReadSettingString("PbrsAlpha", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Retrieve Sort Value")   
                    Else   
                        If Not value.Equals("0") Then   
                            myState.SortState = SortState.Alphabetical   
                        Else   
                            myState.SortState = SortState.Categorized   
                        End If   
                    End If   
                End If   
            End If   
        End Sub   
  
        Public Sub SaveSettingsToStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
  
            If mySvc.MyPackage.packageState IsNot Nothing Then   
                Using rootKey   
                    Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                        Using pbrsKey   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        End Using   
                    End Using   
                End Using   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
            Using rootKey   
                Dim pbrsKey As RegistryKey = rootKey.OpenSubKey(Me.[GetType]().Name)   
                If pbrsKey IsNot Nothing Then   
                    Using pbrsKey   
                        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        Else   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
                        End If   
                    End Using   
                End If   
            End Using   
        End Sub   
    End Class   
End Namespace   
  
Convert C# to VB.NET  
  
```  
  
```c#  
namespace myProfileManagerNameSpace  {  
  
  using System;  
  using System.Runtime.InteropServices;  
  using Microsoft.VisualStudio.Shell;  
  using Microsoft.VisualStudio.Shell.Interop;  
  using Microsoft.Win32;  
  using myPackageNameSpace;  
  
  [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
  internal class MyPackageProfileManager : System.ComponentModel.Component , IProfileManager {  
    internal const int m_supportVer = 8;  
    public void SaveSettingsToXml(IVsSettingsWriter writer) {  
      MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
      if (mySvc != null) {  
        // Information is stored in a StateObject.  
        StateObject myState = mySvc.MyPackage.packageState;  
        writer.WriteSettingString(   
                                  "PbrsAlpha",   
                                  (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
        writer.WriteSettingString(   
                                  "PbrsShowDesc",   
                                  (myState.HelpVisible ? "1" : "0"));  
      }  
    }  
  
    public void LoadSettingsFromXml(IVsSettingsReader reader)  
    {  
  
      int pnMajor, pnMinor, pnBuild;  
      // First, check if data is obtained from the correct major version   
      reader.ReadVersion(pnMajor, pnMinor, pnBuild);  
      if (pnMajor != m_supportVer){  
        reader.ReportError("Unsupported Version");  
      }else{  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        if (mySvc != null){  
          string value;  
          StateObject myState = mySvc.MyPackage.packageState;  
          reader.ReadSettingString("PbrsShowDesc", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Help Visibility Setting");  
          }else{  
            myState.HelpVisible = !value.Equals("0");  
          }  
          reader.ReadSettingString("PbrsAlpha", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }else{  
            if (!value.Equals("0")){  
              myState.SortState = SortState.Alphabetical;  
            }else{  
              myState.SortState = SortState.Categorized;  
            }  
          }  
        }  
      }  
    }  
  
    public void SaveSettingsToStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
  
      if (mySvc.MyPackage.packageState != null) {  
        using (rootKey) {  
          using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
            using (pbrsKey) {  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  
    public void LoadSettingsFromStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
      using (rootKey) {  
        RegistryKey pbrsKey = rootKey.OpenSubKey(this.GetType().Name);  
        if (pbrsKey != null) {  
          using (pbrsKey) {  
            if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }else{  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.IProfileManager>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>   
 [設定のインポート](/visual-cpp/misc/importing-settings)   
 [ユーザー設定のサポート](../extensibility/internals/support-for-user-settings.md)