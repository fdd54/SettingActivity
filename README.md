# SttingActivity
#### 一、实现设置Activity\
##### 设置页面内容\
###### 总共四组设置项\
###### 1、In-line preferences\
  CheckBoxPreference\
###### 2、Dialog-based preferences:\
  EditTextPreference\
  ListPreference Launch preferences\
###### 3、Launch preferences\
  PreferenceScreen: 跳转到另一个PreferenceScreen\
  PreferenceScreen: 启动一个网页\
###### 4、Preference attributes\
  CheckBox: 父选项\
  CheckBox: 子选项，当父选项勾选时呈现\
#### 二、xml设置\
...
<?xml version="1.0" encoding="utf-8"?>
<PreferenceScreen xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <PreferenceCategory
        android:title="In-line preferences"
        android:key="pref_key_storage_settings">
        <CheckBoxPreference
            android:key="pref_check1"
            android:title="Checkbox preference"
            android:summary="This is a checkbox"
            android:defaultValue="true" />
    </PreferenceCategory>
    <PreferenceCategory
        android:title="Dialog-based preferences"
        android:key="pref_key_storage_settings_1">
        <EditTextPreference
            android:defaultValue="context"
            android:key="pref_edit1"
            android:summary="An example that uses an edit dialog"
            android:title="Edit text preference" />
        <ListPreference
            android:defaultValue="true"
            android:key="pref_lp"
            android:title="List preference"
            android:summary="An example that uses an list dialog"
            android:dialogTitle="Choose one"
            android:entries="@array/math_entities"
            android:entryValues="@array/math_values" />
    </PreferenceCategory>
    <PreferenceCategory
        android:title="Launch preferences"
        android:key="pref_key_storage_settings_2">
        <PreferenceScreen
            android:defaultValue="true"
            android:key="pref_ps1"
            android:title="Screen preference"
            android:summary="Shows another screen of preference">
            <CheckBoxPreference
                android:key="pref_check2"
                android:title="Toggle preference"
                android:summary="Preference that is on the next screen but same hierarchy"
                android:defaultValue="false" />
        </PreferenceScreen>
        <Preference
            android:key="pref_intent"
            android:title="Intent preference"
            android:summary="Launches an Activity from an Intent">
            <intent android:action="android.intent.action.VIEW"
                android:data="http://www.example.com" />
        </Preference>
    </PreferenceCategory>
    <PreferenceCategory
        android:title="Preference attributes"
        android:key="pref_key_storage_settings_3">
        <CheckBoxPreference
            android:key="pref_check3"
            android:title="Parent checkbox preference"
            android:summary="This is visually a parent"
            android:defaultValue="false"
            android:disableDependentsState="false" />
        <CheckBoxPreference
            android:dependency="pref_check3"
            android:key="pref_check4"
            android:title="Child checkbox preference"
            android:summary="This is visually a child"
            android:defaultValue="false" />
    </PreferenceCategory>
</PreferenceScreen>
...
