<?xml version="1.0" encoding="utf-8" ?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android" android:compileSdkVersion="33" android:compileSdkVersionCodename="13" android:versionCode="208" android:versionName="4.3-full" package="eu.sisik.hackendebug.full" platformBuildVersionCode="33" platformBuildVersionName="13">
	<uses-sdk android:minSdkVersion="21" android:targetSdkVersion="33" />
	<uses-feature android:name="android.hardware.usb.host" android:required="true" />
	<uses-feature android:name="android.hardware.touchscreen" android:required="false" />
	<uses-permission android:name="android.permission.QUERY_ALL_PACKAGES" />
	<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
	<uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.WAKE_LOCK" />
	<uses-permission android:name="android.permission.USB_PERMISSION" />
	<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
	<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
	<uses-permission android:name="android.permission.FOREGROUND_SERVICE" />
	<uses-permission android:name="com.google.android.gms.permission.AD_ID" />
	<queries>
		<intent>
			<action android:name="android.intent.action.VIEW" />
			<category android:name="android.intent.category.BROWSABLE" />
			<data android:scheme="https" />
		</intent>
		<intent>
			<action android:name="android.support.customtabs.action.CustomTabsService" />
		</intent>
	</queries>
	<uses-permission android:name="com.google.android.finsky.permission.BIND_GET_INSTALL_REFERRER_SERVICE" />
	<uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
	<application android:allowBackup="true" android:appComponentFactory="androidx.core.app.CoreComponentFactory" android:hardwareAccelerated="true" android:icon="@mipmap/logo" android:label="@string/app_name" android:name="eu.sisik.hackendebug.BugjaegerApp" android:resizeableActivity="true" android:supportsRtl="true" android:theme="@style/AppTheme">
		<service android:name="eu.sisik.hackendebug.flashing.FlashingTestService" android:process="flashing.test.process" />
		<meta-data android:name="firebase_analytics_collection_enabled" android:value="false" />
		<meta-data android:name="firebase_crashlytics_collection_enabled" android:value="false" />
		<provider android:authorities="eu.sisik.hackendebug.full.PREFS_PROVIDER_AUTHORITY" android:exported="false" android:name="eu.sisik.hackendebug.utils.PreferenceProvider" />
		<activity android:name="eu.sisik.hackendebug.adb.AdbShellActivity" />
		<activity android:name="eu.sisik.hackendebug.flashing.AndroidImageActivity" />
		<activity android:name="eu.sisik.hackendebug.screencap.ScreenServerActivity" android:process="@string/screenserver_activity_process" />
		<activity android:exported="true" android:name="eu.sisik.hackendebug.SplashActivity" android:windowSoftInputMode="adjustNothing|stateHidden">
			<intent-filter>
				<action android:name="android.intent.action.MAIN" />
				<category android:name="android.intent.category.LAUNCHER" />
			</intent-filter>
		</activity>
		<activity android:exported="true" android:launchMode="singleTask" android:name="eu.sisik.hackendebug.MainActivity" android:resizeableActivity="true" android:theme="@style/AppTheme" android:windowSoftInputMode="adjustNothing|stateHidden">
			<intent-filter>
				<action android:name="android.hardware.usb.action.USB_DEVICE_ATTACHED" />
			</intent-filter>
			<meta-data android:name="android.hardware.usb.action.USB_DEVICE_ATTACHED" android:resource="@xml/device_filter" />
		</activity>
		<receiver android:exported="true" android:name="eu.sisik.hackendebug.UsbReceiver">
			<intent-filter>
				<action android:name="android.hardware.usb.action.USB_DEVICE_ATTACHED" />
			</intent-filter>
			<meta-data android:name="android.hardware.usb.action.USB_DEVICE_ATTACHED" android:resource="@xml/device_filter" />
			<intent-filter>
				<action android:name="android.hardware.usb.action.USB_STATE" />
			</intent-filter>
			<meta-data android:name="android.hardware.usb.action.USB_STATE" android:resource="@xml/device_filter" />
		</receiver>
		<activity android:name="eu.sisik.hackendebug.commands.ShellActivity" android:windowSoftInputMode="adjustResize|stateHidden" />
		<activity android:name="eu.sisik.hackendebug.flashing.FastbootShellActivity" android:windowSoftInputMode="adjustResize|stateHidden" />
		<activity android:name="eu.sisik.hackendebug.packages.ApkListActivity" />
		<activity android:name="eu.sisik.hackendebug.backup.BackupActivity" />
		<service android:name="eu.sisik.hackendebug.connection.PairNotificationService" />
		<service android:name="eu.sisik.hackendebug.flashing.SideloadService" android:permission="android.permission.BIND_JOB_SERVICE" android:process="@string/process_sideload" />
		<service android:name="eu.sisik.hackendebug.utils.FileCacheService" android:process="@string/sync_service_process" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.connection.ScannerService" android:process="@string/scanner_service_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.commands.ShellService" android:process="@string/shell_process_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.device.DeviceInfoService" android:process="@string/device_process_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.screencap.ScreencapService" android:process="@string/screencap_process_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.adb.AdbServerService" android:process="@string/process_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.commands.CommandQueueService" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.commands.CommandProcessingService" android:process="@string/command_process_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.packages.ApkItemLoaderService" android:process="@string/apk_loader_process_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.packages.PackageIntentService" android:process="@string/package_process_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.processes.ProcessIntentService" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.files.FileManagerService" android:process="@string/filemanager_process_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.backup.BackupService" android:process="@string/backupservice_process_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.flashing.FlashingService" android:process="@string/flashing_proc_name" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.connection.ConnectionService" android:process="@string/process_connection_service" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.adb.DeviceListingService" android:process="@string/process_device_listing" />
		<service android:exported="false" android:name="eu.sisik.hackendebug.logcat.LogcatService" android:process="@string/process_logcat" />
		<provider android:authorities="eu.sisik.hackendebug.full.SharedFileProvider" android:enabled="true" android:exported="false" android:grantUriPermissions="true" android:name="eu.sisik.hackendebug.utils.SharedFileProvider">
			<meta-data android:name="android.support.FILE_PROVIDER_PATHS" android:resource="@xml/provider_paths" />
		</provider>
		<uses-library android:name="org.apache.http.legacy" android:required="false" />
		<meta-data android:name="com.google.android.gms.ads.APPLICATION_ID" android:value="ca-app-pub-9950979057979186~8509088871" />
		<activity android:name="eu.sisik.hackendebug.prefs.PrefsActivity" />
		<service android:directBootAware="true" android:exported="false" android:name="com.google.firebase.components.ComponentDiscoveryService">
			<meta-data android:name="com.google.firebase.components:com.google.firebase.crashlytics.ktx.FirebaseCrashlyticsKtxRegistrar" android:value="com.google.firebase.components.ComponentRegistrar" />
			<meta-data android:name="com.google.firebase.components:com.google.firebase.analytics.ktx.FirebaseAnalyticsKtxRegistrar" android:value="com.google.firebase.components.ComponentRegistrar" />
			<meta-data android:name="com.google.firebase.components:com.google.firebase.ktx.FirebaseCommonKtxRegistrar" android:value="com.google.firebase.components.ComponentRegistrar" />
			<meta-data android:name="com.google.firebase.components:com.google.firebase.crashlytics.CrashlyticsRegistrar" android:value="com.google.firebase.components.ComponentRegistrar" />
			<meta-data android:name="com.google.firebase.components:com.google.firebase.analytics.connector.internal.AnalyticsConnectorRegistrar" android:value="com.google.firebase.components.ComponentRegistrar" />
			<meta-data android:name="com.google.firebase.components:com.google.firebase.installations.FirebaseInstallationsRegistrar" android:value="com.google.firebase.components.ComponentRegistrar" />
		</service>
		<provider android:authorities="eu.sisik.hackendebug.full.firebaseinitprovider" android:directBootAware="true" android:exported="false" android:initOrder="100" android:name="com.google.firebase.provider.FirebaseInitProvider" />
		<activity android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize|smallestScreenSize|uiMode" android:exported="false" android:name="com.google.android.gms.ads.AdActivity" android:theme="@android:style/Theme.Translucent" />
		<provider android:authorities="eu.sisik.hackendebug.full.mobileadsinitprovider" android:exported="false" android:initOrder="100" android:name="com.google.android.gms.ads.MobileAdsInitProvider" />
		<service android:enabled="true" android:exported="false" android:name="com.google.android.gms.ads.AdService" />
		<activity android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize|smallestScreenSize|uiMode" android:exported="false" android:name="com.google.android.gms.ads.OutOfContextTestingActivity" />
		<receiver android:enabled="true" android:exported="false" android:name="com.google.android.gms.measurement.AppMeasurementReceiver" />
		<service android:enabled="true" android:exported="false" android:name="com.google.android.gms.measurement.AppMeasurementService" />
		<service android:enabled="true" android:exported="false" android:name="com.google.android.gms.measurement.AppMeasurementJobService" android:permission="android.permission.BIND_JOB_SERVICE" />
		<activity android:exported="false" android:name="com.google.android.gms.common.api.GoogleApiActivity" android:theme="@android:style/Theme.Translucent.NoTitleBar" />
		<meta-data android:name="com.google.android.gms.version" android:value="@integer/google_play_services_version" />
		<activity android:exported="true" android:name="androidx.compose.ui.tooling.PreviewActivity" />
		<uses-library android:name="androidx.window.extensions" android:required="false" />
		<uses-library android:name="androidx.window.sidecar" android:required="false" />
		<service android:exported="false" android:name="com.google.android.datatransport.runtime.backends.TransportBackendDiscovery">
			<meta-data android:name="backend:com.google.android.datatransport.cct.CctBackendFactory" android:value="cct" />
		</service>
		<service android:exported="false" android:name="com.google.android.datatransport.runtime.scheduling.jobscheduling.JobInfoSchedulerService" android:permission="android.permission.BIND_JOB_SERVICE" />
		<receiver android:exported="false" android:name="com.google.android.datatransport.runtime.scheduling.jobscheduling.AlarmManagerSchedulerBroadcastReceiver" />
		<provider android:authorities="eu.sisik.hackendebug.full.androidx-startup" android:exported="false" android:name="androidx.startup.InitializationProvider">
			<meta-data android:name="androidx.emoji2.text.EmojiCompatInitializer" android:value="androidx.startup" />
			<meta-data android:name="androidx.work.WorkManagerInitializer" android:value="androidx.startup" />
			<meta-data android:name="androidx.lifecycle.ProcessLifecycleInitializer" android:value="androidx.startup" />
			<meta-data android:name="androidx.profileinstaller.ProfileInstallerInitializer" android:value="androidx.startup" />
		</provider>
		<service android:directBootAware="false" android:enabled="@bool/enable_system_alarm_service_default" android:exported="false" android:name="androidx.work.impl.background.systemalarm.SystemAlarmService" />
		<service android:directBootAware="false" android:enabled="@bool/enable_system_job_service_default" android:exported="true" android:name="androidx.work.impl.background.systemjob.SystemJobService" android:permission="android.permission.BIND_JOB_SERVICE" />
		<service android:directBootAware="false" android:enabled="@bool/enable_system_foreground_service_default" android:exported="false" android:name="androidx.work.impl.foreground.SystemForegroundService" />
		<receiver android:directBootAware="false" android:enabled="true" android:exported="false" android:name="androidx.work.impl.utils.ForceStopRunnable$BroadcastReceiver" />
		<receiver android:directBootAware="false" android:enabled="false" android:exported="false" android:name="androidx.work.impl.background.systemalarm.ConstraintProxy$BatteryChargingProxy">
			<intent-filter>
				<action android:name="android.intent.action.ACTION_POWER_CONNECTED" />
				<action android:name="android.intent.action.ACTION_POWER_DISCONNECTED" />
			</intent-filter>
		</receiver>
		<receiver android:directBootAware="false" android:enabled="false" android:exported="false" android:name="androidx.work.impl.background.systemalarm.ConstraintProxy$BatteryNotLowProxy">
			<intent-filter>
				<action android:name="android.intent.action.BATTERY_OKAY" />
				<action android:name="android.intent.action.BATTERY_LOW" />
			</intent-filter>
		</receiver>
		<receiver android:directBootAware="false" android:enabled="false" android:exported="false" android:name="androidx.work.impl.background.systemalarm.ConstraintProxy$StorageNotLowProxy">
			<intent-filter>
				<action android:name="android.intent.action.DEVICE_STORAGE_LOW" />
				<action android:name="android.intent.action.DEVICE_STORAGE_OK" />
			</intent-filter>
		</receiver>
		<receiver android:directBootAware="false" android:enabled="false" android:exported="false" android:name="androidx.work.impl.background.systemalarm.ConstraintProxy$NetworkStateProxy">
			<intent-filter>
				<action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
			</intent-filter>
		</receiver>
		<receiver android:directBootAware="false" android:enabled="false" android:exported="false" android:name="androidx.work.impl.background.systemalarm.RescheduleReceiver">
			<intent-filter>
				<action android:name="android.intent.action.BOOT_COMPLETED" />
				<action android:name="android.intent.action.TIME_SET" />
				<action android:name="android.intent.action.TIMEZONE_CHANGED" />
			</intent-filter>
		</receiver>
		<receiver android:directBootAware="false" android:enabled="@bool/enable_system_alarm_service_default" android:exported="false" android:name="androidx.work.impl.background.systemalarm.ConstraintProxyUpdateReceiver">
			<intent-filter>
				<action android:name="androidx.work.impl.background.systemalarm.UpdateProxies" />
			</intent-filter>
		</receiver>
		<receiver android:directBootAware="false" android:enabled="true" android:exported="true" android:name="androidx.work.impl.diagnostics.DiagnosticsReceiver" android:permission="android.permission.DUMP">
			<intent-filter>
				<action android:name="androidx.work.diagnostics.REQUEST_DIAGNOSTICS" />
			</intent-filter>
		</receiver>
		<receiver android:directBootAware="false" android:enabled="true" android:exported="true" android:name="androidx.profileinstaller.ProfileInstallReceiver" android:permission="android.permission.DUMP">
			<intent-filter>
				<action android:name="androidx.profileinstaller.action.INSTALL_PROFILE" />
			</intent-filter>
		</receiver>
		<service android:directBootAware="true" android:exported="false" android:name="androidx.room.MultiInstanceInvalidationService" />
		<activity android:enabled="false" android:exported="false" android:launchMode="singleInstance" android:name="com.google.android.play.core.missingsplits.PlayCoreMissingSplitsActivity" android:process=":playcore_missing_splits_activity" android:stateNotNeeded="true" />
		<activity android:exported="false" android:name="com.google.android.play.core.common.PlayCoreDialogWrapperActivity" android:stateNotNeeded="true" android:theme="@style/Theme.PlayCore.Transparent" />
		<service android:enabled="false" android:exported="true" android:name="com.google.android.play.core.assetpacks.AssetPackExtractionService">
			<meta-data android:name="com.google.android.play.core.assetpacks.versionCode" android:value="11002" />
		</service>
		<service android:enabled="false" android:exported="false" android:name="com.google.android.play.core.assetpacks.ExtractionForegroundService" />
		<meta-data android:name="com.android.dynamic.apk.fused.modules" android:value="base" />
		<meta-data android:name="com.android.stamp.source" android:value="https://play.google.com/store" />
		<meta-data android:name="com.android.stamp.type" android:value="STAMP_TYPE_STANDALONE_APK" />
		<meta-data android:name="com.android.vending.splits" android:value="@xml/splits0" />
		<meta-data android:name="com.android.vending.derived.apk.id" android:value="1" />
	</application>
</manifest>
